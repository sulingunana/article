Önelikle nmap, gobuster ve taramalarını başlatıyoruz
[![site](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/0-1.png)](https://https://tryhackme.com/p/biyik)

[![nmap](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/0-2.png)](https://https://tryhackme.com/p/biyik)
[![gobuster](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/0-3.png)](https://https://tryhackme.com/p/biyik)

gobuster üzerinde görülen sitelere surf yapıyoruz.

[![gobuster](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/0-4.png)](https://https://tryhackme.com/p/biyik)

bize verdiği hint içerisinde ftp veya http üzerinden bağlanmaktan bahsetmiş
biz de ftp üzerinden "anonymous" kullanıcıyla şifresiz olarak bağlanıp şu bilgilere ulaştık

[![ftp](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/1-1.png)](https://https://tryhackme.com/p/biyik)

elimzideki dökümanı ekrana yazdırıyoruz.
 
[![notice.txt](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/1-2.png)](https://https://tryhackme.com/p/biyik)

[![display](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/1-3.png)](https://https://tryhackme.com/p/biyik)

burada elimize hiçbir şey geçmedi

hadi şimdi /uploads/ dizinindeki ftp klasörüyle aynı yer olduğunu anladığımıza göre oraya ters kabuğumuzu yükleyelim. Öncelikle kabuğumuzu alıyoruz.


[![copy](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/2-1.png)](https://https://tryhackme.com/p/biyik)

ardından kendi vpn'imize göre düzenliyoruz.


[![vim](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/2-2.png)](https://https://tryhackme.com/p/biyik)

ulaştığımız bilgiler doğrultusunda ters kabuk yapmak gerektiğini anladık ve
ftp klasörünün içerisine şu şekilde hazırladığımız kabuğu yükledik

[![put-command](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/2-3.png)](https://https://tryhackme.com/p/biyik)

artık kabuğumuz karşı server üzerinde duruyor, kabuğu elde etmek için öncelikle karşı makinein IP adresini ve kabuk içerisindeki portu dinlemeye almamız lazım ve kabuğu çalıştırmak lazım (tıkladık)

[![dinleme](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/2-4.png)](https://https://tryhackme.com/p/biyik)
[![tıklama anı](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/2-5.png)](https://https://tryhackme.com/p/biyik)
ve artık içerdeyiz

[![sign-in-with-webshell](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/2-6.png)](https://https://tryhackme.com/p/biyik)

şimdi de kim olduğumuzu sorguladık ve hala elimizde bir user ismi olmadığını fark ettik. Ama bir ".txt" dosyası fark ettik onu yazdırdık.


[![recipe.txt](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/answer%201.png)](https://https://tryhackme.com/p/biyik)

tarifimizi aldık ve içeriğini bulduk

## Şimdi kişisel dosyaları gezelim


[![lennie-permission-denied](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/3-1.png)](https://https://tryhackme.com/p/biyik)

Biz de girmeye yetkili olduğumuz incidents dizinine girdik ve .pcapng dosyası bulduk. 

[![.pcapng](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/3-2.png)](https://https://tryhackme.com/p/biyik)

onu ters kabuk ile almak için bilgisayarımızda dinleme açıyoruz ve dökümanı çekiyoruz.

[![nc-get-doc](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/3-3.png)](https://https://tryhackme.com/p/biyik)

döküman içerisinde lennie adında bir kullanıcı ismi görüyoruz ve ona ait olabielcek bir şifre buluyoruz

[![write-doc-to-terminal](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/3-4.png)](https://https://tryhackme.com/p/biyik)

[![password-lennie](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/3-5.png)](https://https://tryhackme.com/p/biyik)

Elimizde "lennie" kullanıcısına ait bir password var. ssh ile lennie olarak bağlanıp şifre olarak kullandığımızda lennie olarak sign in olmamız gerek. Komut olarak "ssh lennie@<machine-ip>" girmemiz ve şifreyi girmemiz yeterlidir.

## user flagını buluyoruz
 - "cat user.txt"

root flag ı için kullanıcı değiştirmemiz gerek bunu yapmak için bir tane daha ters kabuk veya yetki yükseltmemiz gerekecek ama lennie grubu beklediğimiz yetkileri alamıyoruz "sudo -l" 

scripts klasörünü inceliyoruz burada "startup_list.txt" ve "planner.sh" adında iki tane dosya bulunmakta, .sh dosyasını görüntülediğimizde üst dizinde olan bir .sh dosyası çalıştırarak .txt dökümanına bir şeyler yansıtmakta. 

burada bir döngü yakalıyoruz ve bu döngüyü kendi amacımız için kullanabiliriz. üst dizini lennie oturumunda yazabilmesi için print.sh dökümanı yetkilerindeyiz. Bu yetkiyi kullanarak olduğu dizindeki yetkileri alabilmek için kabuk komutunu kullanıyoruz. bunu /etc/print.sh scriptinde yapıyoruz. port olarak ilk 8080 kullandım 1234'te zaten bir kabuk kullandığımız için çalışmayacaktır.

[![root-webshell](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/4-1.png)](https://https://tryhackme.com/p/biyik)


[![root](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/4-2.png)](https://https://tryhackme.com/p/biyik)


buradan da root flagını bu şekilde bulduk

[![root-flag](https://github.com/Onur-TURAN/THM/blob/main/Startup/img/4-3.png)](https://https://tryhackme.com/p/biyik)
