#  GERÇEK ZAMANLI YÜZ TANIMA VE DUYGU ANALİZ SİSTEMİ

Bu döküman, **Piksel Mühendisleri** ekibi tarafından yürütülen projenin tüm teknik süreçlerini, haftalık ilerleme raporlarını ve yönetim kararlarını içeren resmi takip dosyasıdır.

---

##  1. Proje Hakkında (Giriş)

Bu projenin temel vizyonu, modern görüntü işleme ve derin öğrenme tekniklerini kullanarak insan-bilgisayar etkileşimini daha anlamlı hale getirmektir. Sistem, standart bir kamera akışı üzerinden anlık olarak yüz tespiti yapabilme ve bu yüzlerden yüksek doğrulukla duygu çıkarımı (mutlu, üzgün, şaşkın vb.) gerçekleştirebilme yeteneğine sahip olacaktır. 

Elde edilen veriler, web tabanlı bir panel üzerinden görselleştirilerek son kullanıcıya veya diğer sistemlere (API) sunulacaktır. Proje; güvenlik, pazarlama ve insan kaynakları gibi çeşitli alanlarda uygulanabilir bir altyapı sunmayı hedeflemektedir.

---

##  2. Ekip ve Görev Dağılımı

Proje süreci, **Scrum** metodolojisine uygun olarak rollerin ve sorumlulukların netleştirilmesiyle yapılandırılmıştır:

| Üye Adı Soyadı | Proje Rolü | Sorumluluk Alanı |
| :--- | :--- | :--- |
| **Şeyma Nur Katar** | **Grup Yöneticisi** | Proje Yönetimi, Koordinasyon, GitHub ve Dökümantasyon Yönetimi |
| **Hatice Kırmızıgül** | **Sistem Analisti** | Proje Analizi, Kapsam Belirleme ve Kullanım Senaryoları |
| **Muhammed Taha Gökdere** | **Yazılım Mühendisi** | Teknik Gereksinimler, Sistem Mimarisi ve Backend Tasarımı |
| **Mehmet Berat Uygur** | **Teknoloji Araştırmacısı** | Kütüphane Fizibilitesi, Model Performans Analizi ve Versiyon Yönetimi |
| **Eren Bilge Koçak** | **Geliştirici (Developer)** | Algoritma Geliştirme, Ortam Kurulumu ve Prototipleme |

---

##  3. Teknoloji Yığını (Tech Stack)

Projenin teknik bütünlüğü ve akademik gereksinimler doğrultusunda şu teknolojilerin kullanılması kararlaştırılmıştır:

* **Ana Programlama Dili:** Python 3.9+
* **Görüntü İşleme:** OpenCV (Open Source Computer Vision Library)
* **Yapay Zeka & Derin Öğrenme:** DeepFace (VGG-Face, Facenet modelleri)
* **Web Framework (Backend):** Flask
* **Arayüz (Frontend):** JavaScript (Chart.js), HTML5, CSS3
* **Veritabanı:** SQLite (Hafif veri kaydı için)

---



# GERÇEK ZAMANLI YÜZ TANIMA VE DUYGU ANALİZ SİSTEMİ 
### 1.1 Proje Analizi ve Kapsam Belirleme (Hatice Kırmızıgül) 

#### Projenin Genel Hedefi:
  Bu projenin amacı, kamera görüntülerinden gerçek zamanlı olarak insan yüzlerini tespit eden ve yüz ifadelerini analiz ederek duygusal durumlarını belirleyen bir sistem geliştirmektir. Sistem, yüz tanıma teknolojisi ve yapay zeka algoritmaları kullanarak kişilerin duygusal durumlarını analiz edecektir. 
  
 #### Projenin Kapsamı:
  Proje kapsamında aşağıdaki işlemler gerçekleşecektir.
- Kamera görüntüsünden yüzlerin algılanması
- Algılanan yüzlerin tanınması ve takip edilmesi
- Yüz ifadelerinden duygu analizi yapılması
- Web tabanlı bir yönetim panelinin oluşturulması
- API aracılığıyla sistem verilerinin diğer uygulamalarla paylaşılması

  #### Temel Özellikler:
 1. Yüz Tanıma ve Takip Modülü
Bu modül kamera görüntüsünden yüzleri tespit eder ve tanınan yüzleri sistem içinde takip eder.

 2. Duygu Analizi
Sistem, yüz ifadelerini analiz ederek kişinin mutlu, üzgün, kızgın veya şaşkın gibi duygularını belirler.

 3. Web Tabanlı Yönetim Paneli
Kullanıcıların sistemi yönetebilmesi ve analiz sonuçlarını görüntüleyebilmesi için web tabanlı bir arayüz sağlanacaktır.

 4. API Entegrasyonu
Sistem verileri API aracılığıyla diğer uygulamalarla paylaşılabilecek ve farklı sistemlerle entegre edilebilecektir.




 ---



###  1.2. Teknik Gereksinimler ve Sistem Analizi (Muhammed Taha Gökdere)

Bu bölüm, derin öğrenme algoritmaları kullanılarak video akışındaki biyometrik verilerin milisaniyeler içinde analiz edilmesi için gereken teknik çerçeveyi tanımlar.

#### **1. Sistemin Amacı ve Kapsamı**
Sistem, "Yüz var mı?", "Bu kim?" ve "Ne hissediyor?" sorularına gerçek zamanlı yanıt vermek üzere tasarlanmıştır.

#### **2. Detaylı Fonksiyonel Gereksinimler (Functional Requirements)**
* **2.1. Görüntü Ön İşleme (Preprocessing):**
    * **FR-1.1 (Gri Ölçeklendirme):** İşlem yükünü azaltmak için renkli kareler (RGB) analizden önce gri ölçeğe (Grayscale) çevrilmelidir.
    * **FR-1.2 (Normalizasyon):** Farklı ışık koşullarında tutarlılık sağlamak için Histogram Eşitleme (Histogram Equalization) tekniği uygulanmalıdır.
* **2.2. Tespit ve Analiz Derinliği:**
    * **FR-2.1 (Çoklu Yüz Tespit):** Sistem, aynı kare içerisinde en az 5 farklı yüzü aynı anda takip edebilmeli ve her birine benzersiz bir ID atamalıdır.
    * **FR-2.2 (Duygu Skorbordu):** Duygu analizi sadece baskın duyguyu değil, her duygunun olasılık yüzdesini (Örn: %70 Mutlu, %20 Nötr, %10 Şaşkın) API üzerinden dönmelidir.
    * **FR-2.3 (Veri Kaydı):** Tespit edilen her "olay" (event); zaman damgası ve koordinat verileriyle birlikte SQLite veya benzeri bir hafif veritabanına kaydedilmelidir.

#### **3. Fonksiyonel Olmayan Teknik Gereksinimler (Non-Functional)**
* **NFR-1 (Gecikme Süresi - Latency):** Görüntünün yakalanması ile duygunun ekrana yazılması arasındaki toplam gecikme (end-to-end latency) **200ms** değerini aşmamalıdır.
* **NFR-2 (Platform Bağımsızlığı):** Flask tabanlı web paneli, hem masaüstü hem de mobil tarayıcılarda (Responsive) sorunsuz çalışmalıdır.
* **NFR-3 (Hata Yönetimi):** Kamera bağlantısı koptuğunda sistem çökmemeli, arayüzde "Kamera Bağlantısı Bekleniyor..." uyarısı vermelidir.
* **NFR-4 (Veri Gizliliği):** KVKK/GDPR uyumluluğu gereği analiz edilen yüz görüntüleri yerel diskte açık bir şekilde tutulmamalı, sadece vektörel veriler (embeddings) saklanmalıdır.

#### **4. Sistem Mimarisi ve Veri Akış Şeması**
Sistem dört ana katman üzerinde kurgulanmıştır:
1.  **Input Layer:** `cv2.VideoCapture(0)` ile yerel veya IP kameradan akış alınır.
2.  **Processing Layer (OpenCV):** Haar Cascades veya DNN modülü ile yüz koordinatları (Bounding Box) belirlenir.
3.  **Analysis Layer (DeepFace):** Kırpılan yüz görüntüsü VGG-Face veya Facenet modellerine gönderilir; duygu vektörü çıkarılır.
4.  **Presentation Layer (Flask & JS):** Sonuçlar WebSockets veya HTTP polling ile arayüze aktarılır; Chart.js ile duygu değişim grafiği çizilir.

#### **5. Kullanım Senaryosu (Use Case Description)**

| Aktör | İşlem | Sistem Tepkisi |
| :--- | :--- | :--- |
| **Sistem Yöneticisi** | Web paneline giriş yapar. | Dashboard üzerinden anlık kamera akışını başlatır. |
| **Sistem** | Bilinmeyen bir yüz tespit eder. | Yüzü çerçeve içine alır, "Bilinmeyen Kişi" yazar ve anlık duygusunu (Örn: Kızgın) belirler. |
| **Sistem** | Duygu eşiği aşılırsa (Örn: %90 Kızgın). | Log sistemine "Yüksek Stres Seviyesi" uyarısı düşer. |

#### **6. Proje Kısıtları (Constraints)**
* **Donanım:** Uygulama, DeepFace modellerinin ağırlığı nedeniyle en az **8 GB RAM** ve **Modern bir CPU/GPU** gerektirir.
* **Yazılım:** Python 3.9+ sürümü zorunludur.


  ---



  ###  1.3. Teknoloji Seçimi ve Gerekçeleri (Mehmet Berat Uygur)

Bu rapor, projenin teknik başarısını, geliştirme hızını ve sistem doğruluğunu optimize etmek amacıyla yapılan teknoloji fizibilitesini içerir.

#### **1. Programlama Dili: Python**
* **Seçim:** **Python**
* **Gerekçe:** Yapay zeka ve bilgisayarla görme alanlarında dünya standardıdır. Kod yazımı hızlı ve anlaşılırdır; TensorFlow, PyTorch ve OpenCV gibi kütüphanelerle yerel entegrasyon sunar.
* **Alternatif:** **C++** (Daha yüksek performans sunsa da geliştirme süreci çok daha uzun ve karmaşıktır).

#### **2. Yüz Tanıma Kütüphanesi: Dlib + Face Recognition**
* **Seçim:** **Dlib + Face Recognition (Python)**
* **Gerekçe:** Dlib, yüz algılama ve landmark (yüz hatları) çıkarma konusunda oldukça güçlüdür. Face Recognition kütüphanesi, Dlib tabanlı çalışarak gerçek zamanlı uygulamalarda yüksek doğruluk ve kullanım kolaylığı sağlar.
* **Alternatif:** **OpenCV Yüz Tanıma Modülü** (Manuel konfigürasyon gerektirir ve doğruluk oranı Dlib’e kıyasla daha düşüktür).

#### **3. Duygu Analizi Kütüphanesi: PyTorch + CNN**
* **Seçim:** **PyTorch + Önceden Eğitilmiş CNN Modelleri**
* **Gerekçe:** PyTorch, derin öğrenme modellerinin geliştirilmesi için esnek ve dinamik bir platform sunar. Önceden eğitilmiş CNN modelleri kullanılarak geliştirme süresi kısaltılırken tahmin doğruluğu maksimize edilir.
* **Alternatif:** **TensorFlow** (Model geliştirme ve konfigürasyon süreci PyTorch'a göre daha karmaşıktır).

#### **4. Geliştirme ve İşbirliği Araçları**
* **Geliştirme Ortamı (IDE):** **VS Code + Jupyter Notebook** (Güçlü kod yönetimi ve interaktif test süreçleri için).
* **Sürüm Kontrolü:** **Git + GitHub** (Dosyaların merkezi bir konumda saklanması, sürüm geçmişinin takibi ve ekip içi senkronizasyon için).

---
