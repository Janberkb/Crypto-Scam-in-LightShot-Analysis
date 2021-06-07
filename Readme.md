# CryptoCurrency Phishing Attack

Notion Link: https://www.notion.so/janberknotes/CryptoCurrency-Phishing-Attack-5824e8b0198144c19952cfbe3a51c384
Merhaba, ben Janberk. Böyle girişleri sevmem ama başka bir şey bulamadım. Bugün Türkçe yazmaya karar verdim. İlginç bir konuya bakacağız bugün aslında. Bir arkadaşım geçen gün bana yazdı ve dedi ki "yahu ben LightShot'ta bir şey buldum". LightShot aracını bilmeyen var ise önce şöyle bir açıklayalım:

> SkillBrains'in anladığım kadarıyla 2010 tarihinde yayınlamış olduğu bir ekran görüntüsü alma ve paylaşma sistemi diyebiliriz. Sistem diyorum çünkü sadece program ile ekran görüntüsü almıyorsunuz, ayrıca bunu [prnt.sc](http://prnt.sc) sitesine yüklüyor ve "**herkese açık**" olan bu ekran görüntüsü bağlantısını arkadaşlarınızla paylaşıyorsunuz.

---

Burada önemli olan nokta bu URL'nin herkes tarafından erişilebilir olması. URL ye sahip herhangi biri sizin ekran görüntünüzü görüntüleyebilir ve bu illegal bir durum değildir.

---

[Burada](https://app.prntscr.com/tr/privacy.html) gizlilik sözleşmesine baktığımızda ilk olarak bize söylenen şey, reklam şirketlerine veya bu verileri kullanmak isteyen yerlere:

- Cihaz Özellikleri (mobil cihazlar için cihaz kimliği dahil)
- İşletim Sistemi
- Tarayıcı Türü
- IP Adresi
- Saklanan çerezlerdeki Kullanıcı Adı
- Oturum açma tarihi ve saati
- Sayfa ve resim görüntüleme istatistikleri ve gelen ve giden bağlantılar

gibi kişisel veri sayılmayan bilgiler. Bu demek oluyor ki siteye girerek bu bilgilerin erişimine izin veriyorsunuz ama bizim dikkatimizi bir başka şey çekiyor.

![CryptoCurrency%20Phishing%20Attack%203e5b07d60f2242dcb5d38208cf06c74b/Untitled.png](CryptoCurrency%20Phishing%20Attack%203e5b07d60f2242dcb5d38208cf06c74b/Untitled.png)

Sitemiz bize diyor ki sizin gönderilerinizi toplamıyoruz işlemiyoruz ama upload edilen tüm fotoğraflar (Profilinizdeki galerinize bile yüklenmiş olsa) **herkese açıktır.** Bir hesabınız olmasa bile upload edilen her fotoğrafın kendi URL'si vardır. Tam URL'ye sahip olan herkesin fotoğrafa erişebilme hakkı mevcuttur. Güvenli bir fotoğraf depolama galerisi değildir diyor.

---

### LightShot URL düzeni

Başta da dediğim gibi arkadaşımın fark ettiği şey olası bir kritik bilgiydi. LightShot fotoğraf URL'lerini incelersek eğer, burada sıralı bir düzenin olduğunu fark ederiz aslında, ki bu zaten uzun süredir herkes tarafından bilinen bir mevzu. Bu URL'ler arasında gezinmek için

![CryptoCurrency%20Phishing%20Attack%203e5b07d60f2242dcb5d38208cf06c74b/Untitled%201.png](CryptoCurrency%20Phishing%20Attack%203e5b07d60f2242dcb5d38208cf06c74b/Untitled%201.png)

Örneğin bu URL'nin rakamlarını değiştirerek vesaire başka ekran görüntülerine de gitmemiz mümkün. Arkadaşım bu URL'ler arasından yabancı bir bitcoin hesabı bulduğunu söyledi. Tabii ekran görüntüsünde yer alan siteyi ve sızan sözde hesabı incelemek istedik çünkü kimse böyle bir bilgiyi LightShot üzerine upload etmez, en azından herkese açık olduğunu bilen birileri yapmaz. Siteyi incelerken sitenin sahte olduğunu ve giriş bilgilerinin tamamen uğraşılmadan belirlendiği sahte bir Phishing sitesi olduğunu gördük. Peki nasıl sahte olduğunu anladık. 

- Öncelikle üye olup gerçekten işleyen bir sistem olup olmadığını test etmek istedik fakat üyelik sistemi çalışmıyordu.
- Kaynak kodlarına bakmak istediğimde gördüğüm şey HTML dosyasının direkt içerisinde JavaScript kodlarının yazıldığıydı.
- İncelemeye devam ettiğimde ilgimi çeken kısım şuydu:

![CryptoCurrency%20Phishing%20Attack%203e5b07d60f2242dcb5d38208cf06c74b/Untitled%202.png](CryptoCurrency%20Phishing%20Attack%203e5b07d60f2242dcb5d38208cf06c74b/Untitled%202.png)

![CryptoCurrency%20Phishing%20Attack%203e5b07d60f2242dcb5d38208cf06c74b/Untitled%203.png](CryptoCurrency%20Phishing%20Attack%203e5b07d60f2242dcb5d38208cf06c74b/Untitled%203.png)

- Bizim bulduğumuz ekran görüntüsündeki kimlik bilgileri direkt buradan belirlenmiş ve kullanılmış oldukça amatör bir şekilde. Ne JavaScript kodları gizli ne de en azından database'den sahte de olsa kimlik bilgisi çekiliyor. Böyle dümdüz buradan alınmış.

### Siteye kimlik bilgisiyle giriş yapalım bakalım neler olacak

![CryptoCurrency%20Phishing%20Attack%203e5b07d60f2242dcb5d38208cf06c74b/Untitled%204.png](CryptoCurrency%20Phishing%20Attack%203e5b07d60f2242dcb5d38208cf06c74b/Untitled%204.png)

Gayet sade bir ekran. Wallet adresleri değiştirilebildiği söylenen bilgiler. Oldukça iyi miktarda Bitcoin ve Etherum. Gel gelelim burada av başlıyor. Eğer kötü niyetli biri iseniz eliniz request transfer kısmından buradaki miktarı kendi  cüzdanınıza almak isteyebilirsiniz.

**Lütfen yapmayın!**

Yine kaynak kodlara baktığımızda bu miktarların da el ile belirlendiğini görüyoruz. 

![CryptoCurrency%20Phishing%20Attack%203e5b07d60f2242dcb5d38208cf06c74b/Untitled%205.png](CryptoCurrency%20Phishing%20Attack%203e5b07d60f2242dcb5d38208cf06c74b/Untitled%205.png)

Hadi biraz BTC çekmeyi deneyelim.

![CryptoCurrency%20Phishing%20Attack%203e5b07d60f2242dcb5d38208cf06c74b/Untitled%206.png](CryptoCurrency%20Phishing%20Attack%203e5b07d60f2242dcb5d38208cf06c74b/Untitled%206.png)

Eveet geldik asıl yerimize. Buraya kadar olan kısımda hep teknik incelemeler yaptık. Bu kısımda eğer kolay ve kötü kazançtan gözünüz dönmedi ise burada artık uyanma vakti gelmiştir. Gerçek olduğunu tespit ettiğiniz bir sıkıntı ise ve gerçekten transfer mümkün ise lütfen hesap sahibini bilgilendirin. Burada insani refleksler ile de anlayabileceğimiz şekilde bize şunu söylüyor özetle:

### "Kardeşim bu parayı istiyorsan önce bi hesabını doğrula ve şu adrese 0.001 Bitcoin at bakalım, sonra bütün parayı çekebilirsin senindir."

İnsanların açgözlülüğünden faydalanarak hem takip edilmesi zor bir şekilde dolandırabiliyorlar hem de dolandırılan kişinin yaptığının da illegal bir durum olması nedeni ile şikayet edilme riskini de en aza indiriyorlar. Kamu Spotu:

### Kolay yoldan para kazanmak denen bir durum yoktur. Kendinizi kandırmayın bu tür tuzaklara düşmeyin.

Teşekkürler.

Daha fazla kaynak için:

[https://www.kaspersky.com.tr/blog/cryptoscam-in-lightshot/9518/](https://www.kaspersky.com.tr/blog/cryptoscam-in-lightshot/9518/)

[https://www.kaspersky.com.tr/blog/cryptoscam-in-discord/9309/](https://www.kaspersky.com.tr/blog/cryptoscam-in-discord/9309/)
