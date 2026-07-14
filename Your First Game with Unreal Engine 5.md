# 🎮 Unreal Engine 5.4 - Blueprints ve Oyun Döngüsü Rehberi (Modül 3)

Bu belge, Unreal Engine 5.4 üzerinde "Blueprints (Görsel Betikleme)" mantığını, oyun döngüsünü (Game Loop) ve temel nesne yönelimli (Object-Oriented) kavramları inceleyen Modül 3'ün detaylı Türkçe özetidir. Rehber, "BoxHunter_V2" adlı eğitim projesi üzerinden yapılandırılmıştır.

---

## 🧩 Nesne Yönelimli (Object-Oriented) Kavramlar

Unreal Engine'deki Blueprint sistemi, Nesne Yönelimli Programlama (OOP) mantığıyla çalışır. Her "sınıf" (Class) başka bir sınıftan türetilebilir.

* **Ebeveyn (Parent) Sınıflar:** Kendisinden türetilen sınıflar için varsayılan özellikleri ve temel verileri belirler.
* **Çocuk (Child) Sınıflar:** Ebeveyn sınıftan türetilirler. Ebeveynin sahip olduğu değişkenleri, fonksiyonları, makroları ve bileşenleri **miras alırlar (inherit)**. Gerektiğinde ebeveynden gelen fonksiyonları geçersiz kılabilir (override) veya genişletebilirler.
* **Miras Alınabilen Öğeler:** Değişkenler, fonksiyonlar, makrolar, bileşenler ve varsayılan ayarlar. (Çocuk sınıf bunu özel olarak değiştirmediği (override) sürece, ebeveynde yapılan her değişiklik çocuğu etkiler).

### Numaralandırıcılar (Enumerators)
Oyun mantığında belirli durumları veya türleri sınıflandırmak için kullanılır. Örneğin eğitim projesindeki platform türleri numaralandırıcılar ile belirlenir:
* `Jump` (Zıplama)
* `Move` (Hareket)
* `Time` (Zaman)
* `None` (Hiçbiri)

---

## 🏗️ Temel Unreal Engine Sınıfları (Classes)

Unreal Engine'de oyunun temelini oluşturan kritik Blueprint sınıfları şunlardır:

### 1. Game Instance (Oyun Örneği)
* **En önemli sınıflardan biridir.**
* Seviyeler (Levels) arasında aktarılması ve korunması gereken kalıcı verileri (persistant data) yönetir.
* Diğer blueprint'lerin aksine asla yok edilemez (destroyed). Oyun açık olduğu sürece arka planda çalışır.
* Farklı blueprint'ler arasında veri göndermek ve projedeki harita yüklemelerini (level loading) koordine etmek için kullanılır.

### 2. Game Mode (Oyun Modu)
* Oyunun temel kurallarını belirler.
* Oyuncuların oyuna nasıl dahil olacağını (spawning), yeni bir seviye yüklendiğinde veya oyun duraklatıldığında (paused) neler olacağını kontrol eder.
* Aynı içerikle farklı oyun türleri yaratmak (örneğin aynı haritada Deathmatch veya Capture The Flag oynamak) için kullanılır.

### 3. Player Controller (Oyuncu Kontrolcüsü)
* Doğrudan fiziksel cihazlardan (klavye, fare, gamepad, VR başlığı) gelen girdileri (inputs) alır.
* Bir "Kukla Ustası (Puppet Master)" gibi çalışır; *Pawn* sınıfından türetilen herhangi bir karakteri veya aracı **kontrol edebilir (Possession)**.
* Üçüncü şahıs bir karakter, uzay gemisi veya araba gibi tamamen farklı türdeki nesnelerin aynı girdi eylemleriyle (Örn: W, A, S, D) kontrol edilmesini sağlar.

### 4. Pawn ve Character (Piyon ve Karakter)
* **Pawn (Piyon):** Player Controller'dan girdi alabilen en temel hareketli sınıftır.
* **Character (Karakter):** Pawn'ın daha gelişmiş bir versiyonudur. İçerisinde özel bir kapsül bileşeni (Capsule Component) ve İskelet Ağı (Skeletal Mesh) barındırır. Canavarlar, karakterler ve genellikle tüm hareketli formlar Pawn sınıfından türetilir.

---

## 🔄 Oyun Döngüsü (Game Loop) Modeli

Eğitim projesinde (`BoxHunter_V2`) oyun döngüsü şu şekilde işler:
1. Oyun **Ana Menü (Main Menu)** ile başlar. Oyuncu başla veya çık komutu verebilir.
2. Başla komutuyla seviye (Level) yüklenir.
3. Oyun süresi bitene veya oyuncu ölene kadar döngü devam eder.
4. Oyun bittiğinde (`GameOver` olayı tetiklendiğinde) oyuncu oyunu yeniden başlatabilir, çıkabilir veya Ana Menüye dönebilir.

**Game Mode Blueprint'indeki Önemli Döngü Olayları:**
* `Event BeginPlay`: Obje yaratıldığında sadece bir kez çalışır. Arayüzü ayarlar ve 1 saniyelik oyun sayacını başlatır.
* `Event GameOver`: Oyun bittiğinde sayacı durdurur ve karakterleri temizler (cleanup).
* `GameTimer`: Oyuna 30 saniyelik bir geri sayım tanımlar. Süre sıfırlandığında `GameOver` olayını çağırır.
* `Event Give Time` / `Event Increase Score`: Oyuncu bir güçlendirici aldığında zamanı veya puanı artıran olaylardır.
* `Event Win The Game`: Oyun kazanıldığında tetiklenir ve ekrandan ölüm bariyerlerini (death volume) temizler.

---

## 🛠️ Projedeki Temel Blueprint Çözümlemeleri

### Player Blueprint (Oyuncu Blueprinti)
Karakterin oyun içindeki hareketlerini ve yeteneklerini kontrol eder.
* İçerisinde; kamera girdileri (Camera Input), standart hareket (W,A,S,D), zıplama yeteneği, ölüm fonksiyonu ve güçlendirmeler (Jump Power-up) bulunur.
* Ayrıca gelişmiş Girdi Eylemleri (Enhanced Input Action) kullanılarak oyundan çıkış (Exit) komutları da buraya eklenmiştir.

### Platform Blueprint (Platform Blueprinti)
Oyundaki zıplanan alanların yapılarını belirler.
* Platformun dönen bir yapıda olup olmadığı, hareket edip etmediği, ne kadar puan veya zaman verdiği gibi parametreleri içerir.
* *Yapıcı Fonksiyon (Constructor):* Platform türünü (Jump, Score, Time vb.) oyun başlarken okur ve buna göre üzerinde güçlendirme nesnesi oluşturur (spawn). Ayrıca dönme ve renk değiştirme animasyonları da bu blueprint içinde yer alır.

---

## ✨ Görsel Efektler ve Arayüz (UI)

### Niagara Visual Effects (Parçacık Sistemi)
Unreal Engine 5'in yeni nesil parçacık efekt sistemidir. Projede kutuların etrafında dönen efektler, dairesel disk şeklindeki patlamalar veya hareketli ışık izleri gibi görsel bildirimler için kullanılmıştır.

### UMG (Unreal Motion Graphics) Kullanıcı Arayüzü
Oyun içi metinlerin ve menülerin düzenlendiği alandır. Projede, oyun durumuna (kazanma, kaybetme, duraklatma) göre yazı renklerinin değişmesi ve farklı hiyerarşik menülerin (Game Over, Next Level vb.) ekranda belirmesi sağlanmıştır.

---

## 📦 Oyunu Paketleme (Packaging)
Oyun geliştirme süreci tamamlandığında oyunu herkesin oynayabileceği bir Windows çalıştırılabilir dosyasına (Executable - .exe) dönüştürme işlemidir:
1. **Project Settings (Proje Ayarları):** Varsayılan başlangıç haritası ve oyun modu seçilir.
2. Üst menüden **Platforms -> Windows -> Package Project** adımları izlenir.
3. Bu işlem projenin büyüklüğüne göre dakikalar veya saatler sürebilir. Eğitim projesinin paketlenmesi yaklaşık 30 dakika sürmüştür.
