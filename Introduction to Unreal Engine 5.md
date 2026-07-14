# 🎮 Unreal Engine 5.4 - Kapsamlı Başlangıç ve Editör Rehberi

Bu belge, oyun geliştirme süreçlerinde Üretken Yapay Zeka kullanımını ele alan eğitimin **Modül 2** içeriğini temel alarak, Unreal Engine 5'in temel özelliklerini, kurulum süreçlerini ve editör arayüzünü (UI) kapsamlı bir şekilde detaylandırmaktadır. Bu modül teori ile birlikte ağırlıklı olarak pratik (uygulamalı) adımlar içermektedir.

---

## 🚀 Unreal Engine 5 Nedir?
Epic Games tarafından geliştirilen Unreal Engine 5, gerçek zamanlı 3D oluşturma (rendering) ve oyun geliştirme dünyasında devrim yaratan en güncel oyun motorudur. Gelişmiş animasyon araçları, yenilenmiş kullanıcı arayüzü ve üstün dünya inşa kapasitesi sunar. Kullanım alanı sadece video oyunlarıyla sınırlı kalmayıp; film sektörü, mimari görselleştirme ve sanal prodüksiyon gibi çoklu endüstrilerde de dönüştürücü bir araç olarak kullanılmaktadır.

### 🏆 Unreal Engine 5 ile Geliştirilen Öne Çıkan Oyunlar
* **ARK II (Studio Wildcard & Grove Street Games):** Dinozorlar ve hayatta kalma unsurları içeren tarih öncesi bir açık dünya oyunu.
* **Black Myth: Wukong (Game Science Interactive):** Çin mitolojisindeki *"Batı'ya Yolculuk"* romanına dayanan yeni nesil aksiyon RPG.
* **Dead by Daylight (Behaviour Interactive):** İkonik katiller ve hayatta kalanları içeren popüler çok oyunculu korku oyunu.
* **Frostpunk 2 (11 Bit Studios):** Donmuş kıyamet sonrası bir dünyada geçen şehir kurma ve hayatta kalma strateji oyunu.
* **Fortnite (Epic Games):** Başlangıçta bir Battle Royale olan oyun, günümüzde herkesin seviyeler tasarlayabildiği devasa bir dünya inşa platformuna (Fortnite Creative) dönüşmüştür.

---

## 🔑 Unreal Engine 5'in Temel Teknolojik Özellikleri

### 1. Nanite (Sanallaştırılmış Mikro Poligon Geometrisi)
* Geleneksel Çokgen Seviyesi (LOD - Level of Detail) modellerine ve manuel optimizasyona olan ihtiyacı ortadan kaldıran çığır açıcı bir teknolojidir.
* Sadece görünür detayları akıllıca işleyerek, milyarlarca poligondan oluşan yüksek kaliteli varlıkların (asset) performans düşüşü yaşanmadan kullanılmasına olanak tanır.
* Sanatçıların teknik optimizasyonlar yerine doğrudan fotogerçekçi sahneler oluşturmaya odaklanmasını sağlar.

### 2. Lumen (Dinamik Küresel Aydınlatma)
* Unreal Engine 5'in en gelişmiş Küresel Aydınlatma (Global Illumination) sistemidir.
* Geleneksel statik aydınlatma ve "Işık Pişirme" (Lightbaking) tekniklerinin aksine; sahnede hareket eden nesnelere veya değişen ışık kaynaklarına anında tepki vererek dinamik ve son derece gerçekçi yansımalar sunar.
* Işığın yüzeylerden sekmesini gerçek dünyadaki gibi simüle ederek yaratıcı süreci inanılmaz derecede hızlandırır.

### 3. Sanal Gölge Haritaları (Virtual Shadow Maps)
* Geleneksel gölge haritalarında görülen tırtıklanma (aliasing) ve düşük çözünürlük sorunlarını çözer.
* Karmaşık geometrilere sahip sahnelerde bile piksel başına (per-pixel) ince ayar yaparak keskin, kararlı ve yüksek detaylı gölgeler üretir.
* Gölgelerin tahsisini dinamik olarak yöneterek yüksek kaliteli gölgelerin getirdiği performans maliyetini düşürür.

### 4. Dünya Bölme Aracı (World Partition Tool)
* Devasa açık dünya ortamlarının yönetimini kolaylaştırır. Büyük haritaları otomatik olarak bir ızgara (grid) sistemine böler.
* Sadece oyuncunun bulunduğu alana ait bölümleri yükleyerek performansı optimize eder (Streaming).
* Ekiplerin aynı haritanın farklı bölümlerinde eşzamanlı ve sorunsuz çalışmasını (collaboration) sağlar.

### 5. MetaHuman Creator
* Geliştiricilerin sadece birkaç dakika içinde yüksek kaliteli, fotogerçekçi ve tam donanımlı (rigged) dijital insanlar yaratmasını sağlayan bulut tabanlı çığır açıcı bir araçtır.
* Yüz hatları, saç, kıyafet ve vücut tiplerinin kolayca özelleştirilmesine imkan tanır ve Unreal Engine'in animasyon sistemleriyle tam uyumlu çalışır.

---

## 🛠️ Unreal Engine 5 Kurulumu ve İlk Proje

1. **Epic Games Launcher Kurulumu:** Epic Games'in resmi web sitesinden Launcher (Başlatıcı) indirilir ve kurulur.
2. **Motor Sürümünü Yükleme:** Launcher içerisindeki "Kütüphane (Library)" sekmesinden en güncel Unreal Engine sürümü (Örn: 5.4.2) seçilir ve yüklenir. Bu sekme aynı zamanda projelerinizi ve Marketplace'ten (Pazar Yeri) indirdiğiniz varlıkları yönettiğiniz yerdir.
3. **İlk Projeyi Başlatma:** 
   * Unreal 5.4.2 başlatılır.
   * `Game` (Oyun) kategorisi seçilir.
   * Şablon olarak `Third Person Template` (Üçüncü Şahıs Şablonu) seçilir.
   * Proje türü olarak `Blueprint` seçilir.
   * Projeye bir isim (örn: Module Two) verilerek "Oluştur" butonuna basılır.

---

## 🖥️ Unreal Editor 5.4 Arayüzü ve Panelleri

Proje açıldığında karşınıza çıkan ana editör arayüzü çeşitli panellerden oluşur:

### 1. Viewport (Görünüm Alanı)
* Geliştiricilerin 3D dünyayı gerçek zamanlı gördüğü, gezindiği ve tasarladığı **ana çalışma alanıdır**.
* Kamerayı hareket ettirmek için standart `W, A, S, D` tuşları ve sağ fare tuşu, yakınlaştırmak için ise fare tekerleği kullanılır. Nesneleri taşımak, döndürmek ve ölçeklendirmek için "Gizmo" adı verilen yön araçları kullanılır.
* Gerçek zamanlı ışın izleme (ray tracing) desteği ve sürükle-bırak varlık yerleştirme özellikleriyle iteratif bir iş akışı sunar.

### 2. Content Browser (İçerik Tarayıcı)
* Projedeki tüm varlıkların (kaplamalar, modeller, ses dosyaları, animasyonlar, blueprint'ler) yönetildiği, içe aktarıldığı ve kategorize edildiği ana depodur.
* Sürükle-bırak mantığıyla varlıkların Viewport'a kolayca eklenmesini sağlar.
* Klasörleme altyapısı ve gelişmiş arama filtreleri sunar.

### 3. Details Panel (Detaylar Paneli)
* Viewport üzerinden seçilen herhangi bir nesneye (ışık, kamera, statik mesh vb.) ait özelliklerin, koordinatların (Transform), materyallerin ve çarpışma (Collision) ayarlarının düzenlendiği yerdir.
* Ekranın sağ tarafında yer alır ve seçilen nesneye göre anlık olarak güncellenir.

### 4. Modes Panel (Modlar Paneli)
* Ekranın sol tarafında bulunur ve projede yapılacak belirli görevler için özel araçlar sunar.
* **Önemli Modlar:** Select (Seçme), Landscape (Arazi), Foliage (Bitki Örtüsü), Modeling (Modelleme), Fracture (Parçalanma) ve UV Editing (UV Düzenleme). İş akışını hızlandıran kritik bir sekmedir.

### 5. Toolbar (Araç Çubuğu)
* Editörün en üst kısmında yer alır. Oyunun test edilmesi için oynat/duraklat/durdur (VCR) butonlarını barındırır.
* Projeyi kaydetme, derleme (build), paketleme (packaging) ve ağ oluşturma (networking) gibi temel proje yönetim araçlarına hızlı erişim sağlar.

### 6. World Outliner (Dünya Ana Hatları)
* Sağ üst kısımda bulunur ve o anki seviyede (level) bulunan tüm nesnelerin hiyerarşik bir listesini gösterir.
* Çok sayıda nesne içeren karmaşık projelerde arama, filtreleme ve klasörleme özellikleri sayesinde düzeni sağlar.

### 7. Blueprint Editor (Görsel Betikleme Editörü)
* Geleneksel programlama (C++ gibi) dillerini yazmaya gerek kalmadan, **düğüm (node) tabanlı** görsel bir arayüz ile oyun mantığı, karakter etkileşimleri ve yapay zeka davranışları oluşturmayı sağlayan güçlü bir sistemdir.
* Modül 3'ün ana odak noktası bu sistem olacaktır.
