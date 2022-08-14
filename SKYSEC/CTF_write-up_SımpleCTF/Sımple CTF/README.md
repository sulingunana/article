Odaya ilk girildiğinde sorulara kısaca baktığımızda NMAP, Gobuster gibi toolları çalıştırmakta fayda olduğunu görüyoruz. Nmap açık portları ve portların numaralarını görmede, işletim sistemi ve versiyonlarını ve kullanılan servisleri görmekte yardımcı olan bir tooldur.
Nmap -h ile parametreleri görmek için kullanabilirz. Burada 1000 in altında kaç port var göreceğiz
-sS tcp syn ile 1000’in altında iki tane port olduğunu gördük 22 ve 80. Portlar.

img1

-sV hem açıkları hem servisleri gösteriyor artı versiyonlar işletim sistemleri de var. -v kullanırsak detaylandıracaktır.

img2

-sV ikisini de Verdi hem açık portlar hem servisler -sS sadece açık portları verdi . Root privilege istiyor. Çünkü NULL, Stealth SYN Scan ve diğerleri gibi bazı gelişmiş port tarama özellikleri, Nmap’in size kullanılabilir sonuçlar vermesi için ham paket verilerine erişmesi gerektiğinden yalnızca kök ayrıcalıklarıyla çalışabilir.8

CVE nin kodları var cve-2019-9053 gibi bunlar zafiyetlerin system versiyonlarına bağlı id leri. Ben şimdi gobuster ile sitenin alt sayfalarına girebilmem lazım . gobuster bir tane txt kullanıyo common txt ile bana alt sayfaları Verdi birinde versiyonunu veren bir sayfa buldum 2.2.8 cmd yazınca cve de aratınca id ler çıktı cve-2019-9053 kodu bu zafiyet ile uyuşuyor. SQL İnjection zafiyeti olduğunu görüyorum.

img3

Yukardaki simple sitesine girdim. Aşağıya bıraktığım versiyonu kullandığını gördüm.
Burada cve sitesindeki aşağıda gördüğümüz kısmında version ile birlikte arama yapıyoruz.

im4
img5
img6

Bir tek simple ve robots çalıştığını görmüştük sitelerden. CVE’ de bulduğumuz zafiyetli kodu indiriyoruz ve aşağıdaki şekilde çalıştırıyoruz. (pythonun kullandığı gerekli kütüphaneler yüklü değil ise “pip install” komutu ile gerekli kütüphaneleri indirip çalıştırmanız gerekebilir)

img7

Zafiyetli python kodunu çalıştıracağız ve sonuçlara bakacağız.

img8

Sonuçlar bize flagleri veriyor. Fakat password şifrelenmiş şekilde burada hashcat toolunu kullanacağız. Bu tool hash algoritmalarına optimize çalışır ve decode eder. Hash algoritmaları parolaları şifreler. Burada bize kullanılacak wordlist gerekiyor, rockyou.txt kullandık. Böylece hash’li kodu decode edeceğiz.

img9

Şifreyi bulduk. Şimdi SSH ile bağlantı kuracağız. Adresi de python çıktısından almıştık. User.txt dosyasını görebilmek için bağlantı kurduktan sonra “ls” komutunu çalıştırdık, okuyabilmek için ise “cat” komutunu çalıştırdık ve diğer flag de buradan geliyor

img10

Pwd komutunu çalıştırarak nerde olduğumu görüyorum sonra kullanıcıların olduğu dizine kadar iniyorum ve iki kullanıcı olduğunu görüyorum mitch and sunbath. Diğer sorunun cevabının sunbath olduğunu görüyorum.

img11
img12

Hangi kullanıcıda olduğumu görmek için üstteki komutu çalıştırıyorum. Kullanıcı mitch usr/bn/vimde çalışıyomuş bunu gördüm. Yetki yükseltmek için sudo vim komutu ile ssh da çalıştırıyoruz. Cevap vim
Sudo vim -c ‘:!/bin/sh’ komutu ile cd /root yapıyoruz sonra dosyaları görmek için ls diyoruz. Root.txt çıkıyor. Bir sonraki flag de burada.

img13
img14
#