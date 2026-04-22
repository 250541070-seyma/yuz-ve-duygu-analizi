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
* **Görüntü İşleme:** OpenCV (Haar Cascade)
* **Derin Öğrenme:** PyTorch (Hugging Face CNN Modelleri)
* **Web Framework (Backend):** Flask & WebSockets
* **Veritabanı:** SQLite (Hafif veri kaydı için)

---



# GERÇEK ZAMANLI YÜZ TANIMA VE DUYGU ANALİZ SİSTEMİ 
## 1.1 Proje Analizi ve Kapsam Belirleme (Hatice Kırmızıgül) 

### Projenin Genel Hedefi:
  Bu projenin amacı, kamera görüntülerinden gerçek zamanlı olarak insan yüzlerini tespit eden ve yüz ifadelerini analiz ederek duygusal durumlarını belirleyen bir sistem geliştirmektir. Sistem, yüz tanıma teknolojisi ve yapay zeka algoritmaları kullanarak kişilerin duygusal durumlarını analiz edecektir. 
  
 ### Projenin Kapsamı:
  Proje kapsamında aşağıdaki işlemler gerçekleşecektir.
- Kamera görüntüsünden yüzlerin algılanması
- Algılanan yüzlerin tanınması ve takip edilmesi
- Yüz ifadelerinden duygu analizi yapılması
- Web tabanlı bir yönetim panelinin oluşturulması
- API aracılığıyla sistem verilerinin diğer uygulamalarla paylaşılması

  ### Temel Özellikler:
 1. Yüz Tanıma ve Takip Modülü
Bu modül kamera görüntüsünden yüzleri tespit eder ve tanınan yüzleri sistem içinde takip eder.

 2. Duygu Analizi
Sistem, yüz ifadelerini analiz ederek kişinin mutlu, üzgün, kızgın veya şaşkın gibi duygularını belirler.

 3. Web Tabanlı Yönetim Paneli
Kullanıcıların sistemi yönetebilmesi ve analiz sonuçlarını görüntüleyebilmesi için web tabanlı bir arayüz sağlanacaktır.

 4. API Entegrasyonu
Sistem verileri API aracılığıyla diğer uygulamalarla paylaşılabilecek ve farklı sistemlerle entegre edilebilecektir.




 ---



##  1.2. Teknik Gereksinimler ve Sistem Analizi (Muhammed Taha Gökdere)

Bu bölüm, derin öğrenme algoritmaları kullanılarak video akışındaki biyometrik verilerin milisaniyeler içinde analiz edilmesi için gereken teknik çerçeveyi tanımlar.

### **1. Sistemin Amacı ve Kapsamı**
Sistem, "Yüz var mı?", "Bu kim?" ve "Ne hissediyor?" sorularına gerçek zamanlı yanıt vermek üzere tasarlanmıştır.

### **2. Detaylı Fonksiyonel Gereksinimler (Functional Requirements)**
* **2.1. Görüntü Ön İşleme (Preprocessing):**
    * **FR-1.1 (Gri Ölçeklendirme):** İşlem yükünü azaltmak için renkli kareler (RGB) analizden önce gri ölçeğe (Grayscale) çevrilmelidir.
    * **FR-1.2 (Normalizasyon):** Farklı ışık koşullarında tutarlılık sağlamak için Histogram Eşitleme (Histogram Equalization) tekniği uygulanmalıdır.
* **2.2. Tespit ve Analiz Derinliği:**
    * **FR-2.1 (Çoklu Yüz Tespit):** Sistem, aynı kare içerisinde en az 5 farklı yüzü aynı anda takip edebilmeli ve her birine benzersiz bir ID atamalıdır.
    * **FR-2.2 (Duygu Skorbordu):** Duygu analizi sadece baskın duyguyu değil, her duygunun olasılık yüzdesini (Örn: %70 Mutlu, %20 Nötr, %10 Şaşkın) API üzerinden dönmelidir.
    * **FR-2.3 (Veri Kaydı):** Tespit edilen her "olay" (event); zaman damgası ve koordinat verileriyle birlikte SQLite veya benzeri bir hafif veritabanına kaydedilmelidir.

### **3. Fonksiyonel Olmayan Teknik Gereksinimler (Non-Functional)**
* **NFR-1 (Gecikme Süresi - Latency):** Görüntünün yakalanması ile duygunun ekrana yazılması arasındaki toplam gecikme (end-to-end latency) **200ms** değerini aşmamalıdır.
* **NFR-2 (Platform Bağımsızlığı):** Flask tabanlı web paneli, hem masaüstü hem de mobil tarayıcılarda (Responsive) sorunsuz çalışmalıdır.
* **NFR-3 (Hata Yönetimi):** Kamera bağlantısı koptuğunda sistem çökmemeli, arayüzde "Kamera Bağlantısı Bekleniyor..." uyarısı vermelidir.
* **NFR-4 (Veri Gizliliği):** KVKK/GDPR uyumluluğu gereği analiz edilen yüz görüntüleri yerel diskte açık bir şekilde tutulmamalı, sadece vektörel veriler (embeddings) saklanmalıdır.

### **4. Sistem Mimarisi ve Veri Akış Şeması**
Sistem dört ana katman üzerinde kurgulanmıştır:
1.  **Input Layer:** `cv2.VideoCapture(0)` ile yerel veya IP kameradan akış alınır.
2.  **Processing Layer (OpenCV):** Haar Cascades veya DNN modülü ile yüz koordinatları (Bounding Box) belirlenir.
3.  **Analysis Layer (DeepFace):** Kırpılan yüz görüntüsü VGG-Face veya Facenet modellerine gönderilir; duygu vektörü çıkarılır.
4.  **Presentation Layer (Flask & JS):** Sonuçlar WebSockets veya HTTP polling ile arayüze aktarılır; Chart.js ile duygu değişim grafiği çizilir.

### **5. Kullanım Senaryosu (Use Case Description)**

| Aktör | İşlem | Sistem Tepkisi |
| :--- | :--- | :--- |
| **Sistem Yöneticisi** | Web paneline giriş yapar. | Dashboard üzerinden anlık kamera akışını başlatır. |
| **Sistem** | Bilinmeyen bir yüz tespit eder. | Yüzü çerçeve içine alır, "Bilinmeyen Kişi" yazar ve anlık duygusunu (Örn: Kızgın) belirler. |
| **Sistem** | Duygu eşiği aşılırsa (Örn: %90 Kızgın). | Log sistemine "Yüksek Stres Seviyesi" uyarısı düşer. |

### **6. Proje Kısıtları (Constraints)**
* **Donanım:** Uygulama, DeepFace modellerinin ağırlığı nedeniyle en az **8 GB RAM** ve **Modern bir CPU/GPU** gerektirir.
* **Yazılım:** Python 3.9+ sürümü zorunludur.


  ---



  ##  1.3. Teknoloji Seçimi ve Gerekçeleri (Mehmet Berat Uygur)

Bu rapor, projenin teknik başarısını, geliştirme hızını ve sistem doğruluğunu optimize etmek amacıyla yapılan teknoloji fizibilitesini içerir.

### **1. Programlama Dili: Python**
* **Seçim:** **Python**
* **Gerekçe:** Yapay zeka ve bilgisayarla görme alanlarında dünya standardıdır. Kod yazımı hızlı ve anlaşılırdır; TensorFlow, PyTorch ve OpenCV gibi kütüphanelerle yerel entegrasyon sunar.
* **Alternatif:** **C++** (Daha yüksek performans sunsa da geliştirme süreci çok daha uzun ve karmaşıktır).

### **2. Yüz Tanıma Kütüphanesi: OpenCV (Haar Cascade)**
* **Durum: Revize Edildi**
* **İlk Planlanan: Dlib + Face Recognition**
* **Nihai Seçim: OpenCV (Haar Cascade)**
* **Gerekçe:** Başlangıçta yüksek doğruluk oranı nedeniyle Dlib kütüphanesi tercih edilmiştir. Ancak ilk prototip testlerinde Dlib'in işlemci (CPU) üzerinde yarattığı yoğun yükün saniyedeki kare sayısını (FPS) ciddi oranda düşürdüğü gözlemlenmiştir. Projenin "gerçek zamanlılık" kriterini korumak adına, çok daha hızlı ve düşük kaynak tüketen OpenCV (Haar Cascade) algoritmasına geçiş yapılmıştır. Bu sayede sistem akıcılığı hedeflenen 200ms gecikme süresinin altına çekilmiştir.

### **3. Duygu Analizi Kütüphanesi: PyTorch + CNN**
* **Seçim:** **PyTorch + Önceden Eğitilmiş CNN Modelleri**
* **Gerekçe:** PyTorch, derin öğrenme modellerinin geliştirilmesi için esnek ve dinamik bir platform sunar. Önceden eğitilmiş CNN modelleri kullanılarak geliştirme süresi kısaltılırken tahmin doğruluğu maksimize edilir.
* **Alternatif:** **TensorFlow** (Model geliştirme ve konfigürasyon süreci PyTorch'a göre daha karmaşıktır).

### **4. Geliştirme ve İşbirliği Araçları**
* **Geliştirme Ortamı (IDE):** **VS Code + Jupyter Notebook** (Güçlü kod yönetimi ve interaktif test süreçleri için).
* **Sürüm Kontrolü:** **Git + GitHub** (Dosyaların merkezi bir konumda saklanması, sürüm geçmişinin takibi ve ekip içi senkronizasyon için).

---



## 1.4. İlk Prototip ve Algoritma Doğrulama (Eren Bilge Koçak)

### **1. Projenin Amacı ve Kapsamı**
Bu projenin temel amacı, bilgisayar kamerası üzerinden alınan canlı video akışını işleyerek, çerçeve içerisindeki insan yüzlerini tespit etmek ve tespit edilen yüzlerdeki anlık mimikleri analiz ederek kişinin duygu durumunu (Mutlu, Üzgün, Kızgın, Şaşkın vb.) gerçek zamanlı olarak sınıflandırmaktır. Proje, insan-bilgisayar etkileşimini (HCI) artırmak ve derin öğrenme (Deep Learning) tabanlı görüntü işleme teknolojilerinin pratik bir uygulamasını geliştirmek amacıyla tasarlanmıştır.

### **2. Teknoloji Seçimi ve Mimari Optimizasyon**
Projenin başlangıç fazında planlanan mimari ile uygulama fazında karşılaşılan donanımsal darboğazlar analiz edilmiş ve sistemin gerçek zamanlı (real-time) çalışabilmesi için mimaride optimizasyonlara gidilmiştir:

* **Programlama Dili:** Python. Yapay zeka ve bilgisayarla görme alanlarında dünya standardı olduğu için tercih edilmiştir.
* **Yüz Tanıma (Face Detection):** Başlangıçta planlanan Dlib kütüphanesi, yüksek işlemci yükü ve FPS düşüşü yarattığı için üretim (production) aşamasında yerini çok daha hafif ve anında tepki veren **OpenCV (Haar Cascade)** algoritmasına bırakmıştır.
* **Duygu Analizi (Emotion Recognition):** Mimari plana sadık kalınarak derin öğrenme tabanlı **PyTorch** framework'ü kullanılmıştır. Hugging Face üzerinden alınan önceden eğitilmiş CNN modeli (`dima806/facial_emotions_image_detection`) entegre edilerek yüksek doğruluk oranlarına ulaşılmıştır.
* **Geliştirme Ortamı:** Kod yönetimi ve entegre kütüphane desteği nedeniyle PyCharm tercih edilmiştir.

### **3. Karşılaşılan Zorluklar ve Geliştirilen Mühendislik Çözümleri**
Geliştirme sürecinde sistemin kararlılığını ve performansını artırmak için iki kritik mühendislik müdahalesi yapılmıştır:

 **A. İnce Mimiklerin Tespitinde Kontrast Optimizasyonu**
Yapay zeka modelinin "Mutlu" veya "Şaşkın" gibi belirgin mimikleri kolayca tespit edebilirken, "Kızgın" veya "Üzgün" gibi ince kas hareketlerini ortam ışığına bağlı olarak kaçırdığı gözlemlenmiştir.
* **Çözüm:** Görüntü işleme hattına `cv2.equalizeHist()` (**Histogram Eşitleme**) fonksiyonu entegre edilmiştir. Bu sayede gri tonlamalı görüntünün kontrastı artırılmış ve yapay zekanın mikro-mimikleri algılama oranı maksimize edilmiştir.

 **B. PyTorch Modelinin Yarattığı FPS Darboğazı ve "Frame Skipping" Algoritması**
PyTorch tabanlı ağır derin öğrenme modelinin saniyede 30 kare (30 FPS) işleme zorunluluğu, sistemde ciddi kasmalar ve donmalar yaratmıştır.
* **Çözüm:** Video akışını akıcı tutmak ve işlemci (CPU) yükünü hafifletmek amacıyla **"Frame Skipping"** (Kare Atlama) mimarisi tasarlanmıştır. Sistemin her karede değil, **sadece her 5 karede bir** duygu analizi yapması sağlanmıştır. Arada kalan karelerde ise hesaplama yapılmayıp son bilinen duygu ekrana yansıtılarak sistem yükü %80 oranında azaltılmış ve pürüzsüz bir kamera deneyimi elde edilmiştir.

 **C. Yüz Tespiti Algoritmasında Performans Odaklı Değişim**
İlk prototip aşamasında kullanılan Dlib kütüphanesinin, her karede (frame) tüm yüz landmarklarını hesaplamaya çalışması CPU üzerinde %90’ın üzerinde bir doluluk yaratmıştır. Bu durum, özellikle düşük donanımlı cihazlarda sistemin kilitlenmesine neden olmuştur.
* **Çözüm:** Bölüm 1.3’te detaylandırıldığı üzere; analiz derinliği ile hız arasındaki dengeyi kurmak amacıyla OpenCV (Haar Cascade) algoritmasına geçilmiştir. Bu sayede yüz tespit hızı milisaniyeler seviyesine indirilmiş ve sistemin genel akıcılığı korunmuştur.

### **4. Sistem Testleri ve Çalışma Görüntüleri**
Aşağıda, optimize edilmiş sistemin canlı ortamda yüzü tespit ettiği ve "Frame Skipping" mimarisiyle FPS kaybı yaşamadan anlık duygu durumunu sınıflandırdığı çalışma anına ait ekran görüntüsü yer almaktadır:

![IMG_0304](https://github.com/user-attachments/assets/2e9a4ca7-698a-48cc-a23d-37590fbe4c08)


### **5. Sonuç ve Değerlendirme**
Geliştirilen sistem; OpenCV'nin hızını ve PyTorch'un derin öğrenme kapasitesini aynı potada eriterek başarılı bir hibrit mimari sunmuştur. Geliştirme aşamasında karşılaşılan donanım limitleri (FPS düşüşleri), yazılımsal optimizasyonlarla (Frame Skipping ve Histogram Eşitleme) aşılarak projenin "gerçek zamanlı çalışma" gereksinimi tam anlamıyla karşılanmıştır.

---

## 1.5. GENEL DEĞERLENDİRME VE GELECEK ÇALIŞMALAR
Bu proje; kısıtlı donanım kaynakları altında, Derin Öğrenme (Deep Learning) ve Bilgisayarlı Görme (Computer Vision) tekniklerinin hibrit bir mimariyle nasıl optimize edilebileceğini başarıyla kanıtlamıştır. Geliştirilen sistem, saniyede 30 kare (30 FPS) işleme kapasitesini zorlamadan, kullanıcıya akıcı ve doğru bir duygu analizi deneyimi sunmaktadır.
Gelecek aşamalarda projenin şu yönlerde geliştirilmesi hedeflenmektedir:
* **Model Hafifletme (Quantization):** PyTorch modelinin boyutu ve işlem yükü, "Model Quantization" teknikleriyle optimize edilerek sistemin mobil cihazlarda veya gömülü sistemlerde (Raspberry Pi vb.) çalışması sağlanabilir.
* **Veri Seti Genişletme:** Daha geniş ve çeşitli (farklı yaş, etnik köken, ışık koşulları) veri setleriyle eğitim yapılarak "Kızgın" ve "Üzgün" gibi tespit edilmesi güç mikro-mimiklerin doğruluk oranı artırılabilir.
* **Bulut Entegrasyonu:** Analiz edilen verilerin anonimleştirilerek bulut tabanlı bir veritabanında toplanması ve Büyük Veri (Big Data) analizi ile tüketici davranışları raporlama modülünün eklenmesi planlanmaktadır.




# YÜZ TANIMA VE DUYGU ANALİZİ SİSTEMİ: 2. HAFTA ANALİZ VE TASARIM DÖKÜMANTASYONU
1. PROJE GENEL GİRİŞİ
Bu döküman, Fırat Üniversitesi Yazılım Mühendisliği Bölümü bünyesinde yürütülen "Yüz Tanıma ve Duygu Analizi Sistemi" projesinin ikinci hafta çalışmalarını kapsamaktadır. Projenin temel amacı; kamera görüntüleri üzerinden gerçek zamanlı yüz tespiti yaparak, tespit edilen bireylerin duygusal durumlarını yapay zeka algoritmaları ile analiz eden entegre bir sistem geliştirmektir.

İkinci hafta çalışmaları kapsamında, sistemin teknik mimarisi belirlenmiş, kullanılacak algoritmaların performans analizleri yapılmış ve modüller arası veri akışı şemalandırılmıştır. Bu süreçte hız, doğruluk ve düşük gecikme süresi (latency) temel mühendislik kriterleri olarak baz alınmıştır.
## TEKNOLOJİ SEÇİMİ VE GEREKÇELENDİRME RAPORU (HAFTA 2)
Hazırlayan: Şeyma Nur Katar
Proje görevi : Teknoloji Seçimi & Gerekçelendirme
Proje: Yüz Tanıma ve Duygu Analizi Sistemi

### 1. GİRİŞ
Bu döküman; sistemin geliştirilmesinde kullanılacak olan yazılım dillerinin, kütüphanelerin ve frameworklerin seçim süreçlerini, bu seçimlerin nedenlerini, avantajlarını ve olası risklere karşı geliştirilen çözüm önerilerini kapsamaktadır. Projenin teknik bütünlüğü ve akademik gereksinimler doğrultusunda belirlenen bu teknolojiler, tüm ekip üyeleri için bağlayıcıdır.


 ### 2. TEKNOLOJİ ANALİZİ VE SEÇİM GEREKÇELERİ
Teknoloji	Seçim Amacı	Avantajı	Dezavantajı / Risk
Python 3.9+	Ana Programlama Dili	AI/ML kütüphane desteği, hızlı prototipleme ve geniş topluluk desteği.	C++'a göre daha yavaş çalışma hızı (GIL kısıtlaması).
OpenCV	Görüntü İşleme	Gerçek zamanlı (Real-time) işlem hızı, düşük kaynak tüketimi.	Karmaşık ışıklandırma koşullarında doğruluk kaybı riski.
DeepFace	Duygu Analizi Modeli	Birden fazla CNN modelini (VGG-Face, Facenet) tek çatıda desteklemesi.	Yüksek işlem yükü (CPU/GPU) gereksinimi.
Flask	Backend Framework	Mikro-mimari yapısı sayesinde hafif, hızlı ve esnek entegrasyon.	Çok yüksek trafikli sistemlerde ek yapılandırma gerektirmesi.
JavaScript	Frontend & Dashboard	Dinamik veri görselleştirme (Chart.js) ve zengin kullanıcı etkileşimi.	Tarayıcı uyumluluğu ve performans takibi gereksinimi.




 ### 3. DERİNLEMESİNE DEĞERLENDİRME VE RİSK ANALİZİ
3.1. Neden Python ve Flask?
Projenin temelinde yer alan derin öğrenme modellerinin en kararlı performansı Python ekosisteminde (PyTorch/TensorFlow) vermesi nedeniyle Python ana dildir. Flask ise, projenin modüler yapısını korumak ve sistemler arası veri akışını (API katmanı) karmaşıklaştırmadan yönetmek için tercih edilmiştir.
3.2. OpenCV (Haar Cascade) Tercih Nedeni
Dlib veya MTCNN gibi ağır modeller yerine OpenCV Haar Cascade seçilmiştir.
•	Gerekçe: Gerçek zamanlı analizde FPS değerini korumak, doğruluğu bir miktar feda edip akıcılığı artırmaktan geçmektedir.
•	Risk Yönetimi: Düşük ışıkta yüz kaçırma ihtimaline karşı, görüntü ön işleme katmanında Histogram Eşitleme(Equalization) kullanılarak kontrast artırılacaktır.

### 4. OLASI RİSKLER VE MÜHENDİSLİK ÇÖZÜMLERİ
[!IMPORTANT] Projenin başarısı, aşağıdaki iki temel riskin yönetilmesine bağlıdır:
Risk 1: Gecikme (Latency) Sorunu Derin öğrenme modelleri her karede analiz yaparsa sistem 30 FPS'den 5-10 FPS seviyelerine düşebilir.
•	 Çözüm: "Frame Skipping" (Kare Atlama) mimarisi uygulanacaktır. Yüz tespiti her karede yapılırken, ağır duygu analizi işlemleri her 5 karede bir gerçekleştirilecektir.
Risk 2: Donanım Yetersizliği ve FPS Darboğazı Sistemin düşük işlemci gücüne sahip cihazlarda (Laptop CPU) donma yapma ihtimali mevcuttur.
•	 Çözüm: Model Quantization (Hafifletme) teknikleri ve ağırlık optimizasyonları kullanılarak model boyutu ve işlemci yükü minimuma indirilecektir.


### 5. SONUÇ
Seçilen hibrit teknoloji yığını; projenin gerçek zamanlı çalışma, düşük gecikme süresi ve web tabanlı izlenebilirlikhedeflerini karşılayacak en optimize yapıyı sunmaktadır. Grup yöneticisi olarak, tüm birimlerin (Analiz, Yazılım, UI/UX) bu teknik çerçeveye sadık kalarak 2. hafta görevlerini tamamlaması kararlaştırılmıştır.

## KAMERA GÖRÜNTÜLERİNDEN YÜZ TANIMA VE TAKİP MODÜLÜ GEREKSİNİM ANALİZİ RAPORU
 Hazırlayan: Hatice Kırmızıgül
 Proje: Yüz Tanıma ve Duygu Analizi Sistemi
 Görevi: Yüz Tanıma ve Takip Modülü Analizi

### 1. Giriş
Bu rapor, kamera görüntülerinden gerçek zamanlı yüz tanıma ve takip modülünde kullanılacak yöntemlerin belirlenmesi amacıyla hazırlanmıştır. Sistem tasarımında hem işlem hızı hem de doğruluk dikkate alınmıştır. Gerçek zamanlı çalışacak bir yapıda yüzün hızlı tespit edilmesi ve kareler arasında kaybolmadan takip edilmesi hedeflenmiştir.

### 2. Yüz Tanıma Algoritması Seçimi
Projede yüz tespiti için OpenCV içinde bulunan Haar Cascade algoritmasının kullanılması uygun görülmüştür.
Seçilme nedenleri:
•	Gerçek zamanlı çalışmada hızlı sonuç vermesi 
•	CPU üzerinde düşük yük oluşturması 
•	Hazır eğitimli veri setleri ile kolay uygulanabilmesi 
Dezavantajı:
•	Düşük ışıkta doğruluk düşebilir 
•	Baş eğimlerinde hata yapabilir 
Bu riskleri azaltmak için görüntü ön işleme aşamasında histogram eşitleme uygulanacaktır.
Alternatif olarak HOG ve CNN tabanlı yöntemler değerlendirilmiştir. Ancak HOG daha fazla işlem yükü oluşturduğu, CNN tabanlı yöntemler ise donanım ihtiyacını artırdığı için başlangıç aşamasında tercih edilmemiştir.

### 3. Takip Yöntemi Seçimi
Yüz tespit edildikten sonra kareler arasında takibin sürdürülebilmesi için Kalman filtresi kullanılacaktır.
Kullanım amacı:
•	Yüz kısa süre kaybolduğunda tahmin yapabilmek 
•	Hareketi daha kararlı izlemek 
•	Titremeyi azaltmak 
Kalman filtresi, tespit edilen yüz koordinatlarını kullanarak sonraki karede olası konumu hesaplayacaktır.
MeanShift yöntemi de değerlendirilmiştir ancak renk değişimlerinden etkilenebildiği için ana yöntem olarak seçilmemiştir.

### 4. Performans Gereksinimleri
Sistemin minimum performans hedefleri aşağıdaki şekilde belirlenmiştir:
•	Minimum 20 FPS 
•	İdeal 25–30 FPS 
•	Kontrollü ortamda %90 doğruluk 
•	Düşük ışıkta %80 doğruluk 
Duygu analizi gibi ağır işlemler her karede yapılmayacak, her 5 karede bir çalıştırılacaktır. Böylece işlem yükü azaltılacaktır.

### 5. Sonuç
Yapılan değerlendirme sonucunda sistem için en uygun yapı:
•	Yüz tespiti: Haar Cascade 
•	Takip: Kalman filtresi 
•	Ağır analizler: Belirli aralıklı çalışma 
Bu yapı hem gerçek zamanlı çalışma hem de donanım verimliliği açısından proje gereksinimlerine uygundur.

## DUYGU ANALİZİ ALGORİTMASI ARAŞTIRMA VE KARŞILAŞTIRMA RAPORU
Hazırlayan: Muhammed Taha Gökdere
Proje: Yüz Tanıma ve Duygu Analizi Sistemi
Görevi: Duygu Analizi Algoritma Araştırması ve Seçimi

### 1. Derin Öğrenme Tabanlı Algoritmaların Analizi
Duygu analizi sistemleri genellikle bir Yüz Tespiti (Detection) ve ardından bir Sınıflandırma (Classification) hattı üzerinden çalışır.

A. DeepFace (Ensemble Framework)
DeepFace; Google (FaceNet), Facebook (DeepFace) ve Oxford (VGG-Face) gibi devlerin modellerini tek çatıda toplayan bir kütüphanedir.

Mimari: Birden fazla modelin ağırlıklarını kullanabilen hibrit bir yapı.

Duygular: Mutluluk, üzüntü, korku, öfke, şaşkınlık, tiksinti, nötr.

B. VGG-Face (VGG-16 Tabanlı)
Aslen yüz tanıma için geliştirilmiş olsa da, Transfer Learning yöntemiyle duygu analizi için en sık özelleştirilen modeldir.

Karakteristik: Yüzün geometrik özelliklerinden ziyade dokusal (texture) özelliklerine odaklanır.

C. AffectNet (Veri Kümesi ve Model Standartı)
1 milyondan fazla görüntüyü içeren dünyanın en büyük duygu veri kümesidir. Bu veri kümesiyle eğitilen modeller (genellikle ResNet tabanlı) literatürde altın standart kabul edilir.

### 2. Teknik Karşılaştırma Tablosu
Kriter	DeepFace (Default)	VGG-Face (Fine-tuned)	AffectNet Tabanlı ResNet
Doğruluk (%)	~%91 - %93	~%88 - %90	~%60 - %70 (Vahşi Ortam)
İşlem Hızı	Orta (15-20 FPS)	Yavaş (Yüksek Parametre)	Hızlı (Optimize edilirse)
Duygu Etiketleri	7 Temel Duygu	7 Temel Duygu	8+ Duygu
Kaynak (CPU)	Yüksek Kullanım	Çok Yüksek (Hantal)	Orta
Kaynak (GPU)	4GB+ VRAM İdeal	8GB+ VRAM Önerilir	2GB+ VRAM Yeterli


### 3. Proje Gereksinimlerine Göre Algoritma Seçimi
Seçilen Algoritma: DeepFace Framework (Backend: RetinaFace + Model: ResNet)

Seçim Gerekçeleri:
Entegrasyon Kolaylığı: Python ortamında hazır fonksiyonlarla gelmesi geliştirme süresini ciddi oranda düşürür.

Yüz Tespiti Üstünlüğü: İçerisindeki RetinaFace dedektörü, maskeli veya yan dönmüş yüzlerde bile %90+ doğruluk sunar.

Çok Yönlülük: Sadece duygu değil; yaş, cinsiyet ve ırk gibi metrikleri de aynı anda analiz edebilir.

Dinamik Donanım Desteği: Hem CPU'da stabil çalışır hem de NVIDIA GPU'larda CUDA desteğiyle gerçek zamanlı analiz yapabilir.

### 4. Uygulama Stratejisi (Nasıl "Baya İyi" Olur?)
Sistemin kararlılığını artırmak için şu iki yöntem uygulanacaktır:

Zaman Damgalı Filtreleme (Sliding Window): Tek bir karede anlık hatalı tespitleri engellemek için son 10 karedeki sonuçların medyanı veya modu alınarak "duygusal süreklilik" sağlanacaktır.

Aydınlatma Normalizasyonu: Görüntü modele girmeden önce Histogram Eşitleme (CLAHE) uygulanacaktır. Bu, karanlık ortamlarda kaş çatıklığı gibi mikro ifadelerin daha iyi seçilmesini sağlar.

### 5. Sonuç
Proje için DeepFace, sunduğu kütüphane desteği ve yüksek doğruluk oranıyla en rasyonel seçimdir. Ancak sistemin "gerçekten iyi" çalışması için sadece modele güvenilmemeli; görüntü ön işleme ve sonuçların zamansal filtrelenmesi teknikleri mutlaka tasarıma dahil edilmelidir.

## API ENTEGRASYONU PLANLAMASI VE VERİ AKIŞI ŞEMASI
Hazırlayan: Eren Bilge Koçak
Proje: Yüz Tanıma ve Duygu Analizi Sistemi
Görevi: API Entegrasyonu ve Sistemler Arası Veri Akışı

### 1. GİRİŞ VE GÖREV AMACI
Bu rapor, sistemin elde ettiği verilerin dış sistemlerle (Güvenlik, İK Yazılımları, Pazarlama Otomasyonu) gerçek zamanlı ve güvenli bir şekilde entegre edilebilmesi için tasarlanan API mimarisini kapsamaktadır. Tasarlanan mimari, FastAPI kullanılarak ayağa kaldırılmış ve başarıyla test edilmiştir.

### 2. MİMARİ KARARLAR VE KULLANILAN TEKNOLOJİLER
API Mimarisi: REST (Representational State Transfer)

Neden: Günümüz modern web servislerinde standarttır. Mikroservis mimarisine uygun, bağımsız ve hızlı çalışmaya olanak tanır. Python tabanlı FastAPI framework'ü ile asenkron (hızlı) uç noktalar oluşturulmuştur.

Veri Formatı: JSON (JavaScript Object Notation)

Neden: Hafif, okunabilir ve minimum bant genişliği harcar. Python sözlük yapılarıyla (dictionary) doğrudan uyumludur.

Kimlik Doğrulama: API Key (API Anahtarı)

Neden: Sistemden sisteme (Server-to-Server) iletişimde OAuth gibi karmaşık süreçler yerine, düşük gecikme sağlayan ve güvenliği elden bırakmayan statik anahtar yöntemi tercih edilmiştir.

### 3. SİSTEMLER ARASI VERİ AKIŞI ŞEMASI
Sistemdeki veri trafiği şu hiyerarşi ile yönetilmektedir:

Kamera Kaynağı: Görüntü frame'lerini yakalar.

Analiz Motoru: Yüz ve Duygu analizi sonuçlarını üretir.

FastAPI Sunucusu: Gelen veriyi doğrular (API Key kontrolü).

Dış Sistemler: Doğrulanmış JSON verisi ilgili birimlere (Güvenlik, İK vb.) iletilir.
![Ekran Resmi 2026-04-09 00 06 36](https://github.com/user-attachments/assets/91e62a72-0b15-4265-a6c7-dabc624a4be0)


### 4. ÇALIŞAN SİSTEMİN KANITLARI VE TEST SONUÇLARI
A. API Kaynak Kodları (FastAPI Implementation)
<img width="1470" height="956" alt="Ekran Resmi 2026-04-09 00 07 52" src="https://github.com/user-attachments/assets/b0a2481a-4c34-4cdb-a6f1-3bb3c076b718" />

B. Test Sonuçları
Uvicorn Sunucusu: Yerel ortamda (localhost) başarıyla başlatıldı.

Swagger UI (HTTP 200): Yapılan entegrasyon testlerinde yetkili erişim sağlanmış ve sistem "200 OK" yanıtı ile başarılı veri aktarımını doğrulamıştır.
![Görüntü](https://github.com/user-attachments/assets/6f2d11c4-6386-4e58-b36d-87bc77719cae)


### 5. SONUÇ
Yüz tanıma ve duygu analizi motorunun dış dünya ile haberleşmesini sağlayacak olan REST API altyapısı, güvenli ve yüksek performanslı bir şekilde çalışır durumda teslim edilmiştir.

## WEB TABANLI YÖNETİM PANELİ TASARIM VE KULLANICI SENARYOLARI
Hazırlayan: Mehmet Berat Uygur
Proje: Yüz Tanıma ve Duygu Analizi Sistemi
Proje Görevi: Web Tabanlı Yönetim Paneli Tasarımı

### 1. PROJE TANIMI
Bu proje, yüz tanıma ve duygu analizi yapan bir sistemin verilerini merkezi bir noktadan yönetmek ve izlemek amacıyla geliştirilecek web tabanlı bir yönetim panelini kapsamaktadır. Panel sayesinde yöneticiler sistemi gerçek zamanlı olarak izleyebilir, kullanıcı yetkilendirmelerini yönetebilir, analiz sonuçlarını detaylı olarak görüntüleyebilir ve stratejik raporlar oluşturabilir.

### 2. PANELDE GÖRÜNTÜLENECEK BİLGİLER
2.1. Dashboard (Ana Sayfa)
Günlük tespit edilen toplam kişi sayısı.

Duygu analizi dağılım verileri (mutlu, üzgün, nötr vb.).

Sistem üzerinden gerçekleşen son aktiviteler ve bildirimler.

Analiz motorunun güncel durumu (aktif/pasif kontrolü).

#### 2.2. Yüz Tanıma Sonuçları
Tanımlanan bireylerin isimleri veya benzersiz ID bilgileri.

Verinin işlendiği tarih ve saat bilgisi.

Kaynak kamera bilgisi.

Algoritmanın doğruluk güven skoru (%).

Tespit anına ait görüntü önizlemesi.

#### 2.3. Duygu Analizi Sonuçları
Tespit edilen temel duygu durumu.

Yüz tespiti ile sağlanan eşleşme verisi.

Analizin gerçekleştirildiği zaman dilimi.

Tahmin güven oranı.

Grafiksel gösterimler (pie chart / bar chart).

#### 2.4. Sistem Logları
Kritik hata ve istisna kayıtları.

Kullanıcı sisteme giriş ve çıkış kayıtları.

Sistem olayları ve olay bazlı log filtreleme özellikleri (tarih ve tür).

### 3. KULLANICI İŞLEVLERİ
3.1. Kullanıcı Yönetimi
Yeni kullanıcı hesabı tanımlama.

Mevcut kullanıcı kayıtlarını silme veya pasifize etme.

Rol atama süreçleri (Admin / Operatör / İzleyici).

Şifre sıfırlama ve hesap kurtarma işlemleri.

#### 3.2. Sistem Ayarları
Yeni kamera kaynağı ekleme veya mevcut kaynakları çıkarma.

Yapay zeka model parametreleri ve eşik (threshold) ayarları.

Kritik durum bildirim ve uyarı ayarları.

Arayüz dil seçenekleri ve görsel tema (koyu/açık) tercihleri.

#### 3.3. Raporlama
Belirli tarih aralıklarına göre özelleştirilmiş rapor üretimi.

Verilerin PDF veya Excel formatında dışa aktarımı.

Periyodik duygu analizi istatistik raporları.

Kişi veya grup bazlı analiz dökümleri.

### 4. KULLANICI ROLLERİ VE YETKİLERİ
Rol	Yetkiler
Admin	Sistemdeki tüm yapılandırma, kullanıcı yönetimi ve veri işlemlerini gerçekleştirir.
Operatör	Veri görüntüleme, analiz sonuçlarını inceleme ve rapor oluşturma yetkisine sahiptir.
İzleyici	Sadece dashboard ve canlı verileri görüntüleme yetkisine sahiptir; işlem yetkisi yoktur.
### 5. KULLANICI ARAYÜZÜ (UI) TASARIM ESASLARI
Navigasyon: Hızlı erişim sağlayan sol menü (sidebar) yapısı.

Üst Panel: Kullanıcı profili, bildirim merkezi ve sistem durumu göstergeleri.

Veri Görselleştirme: Kart bazlı dashboard tasarımı ile modüler yapı.

Görsel Tema: Kullanıcı konforu için koyu ve açık tema desteği.

### 6. WIREFRAME (TEL ÇERÇEVE) TASARIMLARI
#### 6.1. Dashboard Taslağı
Plaintext
-----------------------------------------------------------------------
| LOGO | DASHBOARD | ANALİZ SONUÇLARI | KULLANICI YÖNETİMİ | AYARLAR  |
-----------------------------------------------------------------------
|        |   [ Toplam Kişi ]   |   [ Duygu Dağılım Grafiği ]          |
|  MENÜ  |       2.450         |         (Pie Chart)                  |
|        |------------------------------------------------------------|
| SIDEBAR|               [ SON AKTİVİTE AKIŞI ]                       |
|        | ID: 250 | İsim: Şeyma | Duygu: Mutlu | Saat: 10:45         |
-----------------------------------------------------------------------
#### 6.2. Kullanıcı Yönetimi Taslağı
Plaintext
-----------------------------------------------------------------------
| [ KULLANICI LİSTESİ ]                                 [ + YENİ EKLE]|
-----------------------------------------------------------------------
| İSİM         | ROL       | DURUM    | İŞLEM                         |
|--------------|-----------|----------|-------------------------------|
| Ahmet Yılmaz | Admin     | Aktif    | [Düzenle] [Sil]               |
| Ayşe Demir   | Operatör  | Aktif    | [Düzenle] [Sil]               |
-----------------------------------------------------------------------
### 7. KULLANICI AKIŞ ŞEMALARI
#### 7.1. Sisteme Giriş Akışı
Başla

Giriş Ekranı (Kullanıcı Adı / Şifre)

Kimlik Doğrulama (JWT Kontrolü)

Dashboard Erişimi

#### 7.2. Kullanıcı Ekleme Akışı
Dashboard üzerinden Kullanıcı Yönetimi sekmesine geçiş

"Yeni Kullanıcı Ekle" butonunun tetiklenmesi

Form bilgilerinin girişi ve rol ataması

Veritabanına kayıt ve işlem başarı mesajı

#### 7.3. Rapor Oluşturma Akışı
Dashboard üzerinden Raporlar sekmesine geçiş

Filtreleme seçeneklerinin (Tarih / Kamera / Kişi) belirlenmesi

"Rapor Oluştur" komutunun verilmesi

PDF veya Excel çıktı dosyasının indirilmesi

### 8. TEKNİK ÖNERİLER VE TEKNOLOJİ YIĞINI
Frontend: React veya Vue.js (Dinamik ve hızlı arayüz performansı için).

Backend: FastAPI (Python) veya Node.js (Asenkron veri işleme için).

Veritabanı: PostgreSQL (İlişkisel veri güvenliği için).

Grafik Kütüphanesi: Chart.js (Dinamik veri görselleştirme için).

Kimlik Doğrulama: JWT (JSON Web Token) tabanlı güvenli oturum yönetimi.

### 9. SONUÇ
Tasarlanan bu yönetim paneli, sistemin ürettiği karmaşık verileri merkezi bir noktada toplayarak kullanım kolaylığı, anlık veri takibi ve derinlemesine analiz kabiliyeti sunacaktır. Modüler yapısı sayesinde gelecekteki yeni analiz gereksinimlerine göre kolayca genişletilebilir bir mimariye sahiptir.
 

# 1. GENEL GİRİŞ

Bu döküman, Fırat Üniversitesi Yazılım Mühendisliği Bölümü bünyesinde yürütülen *"Yüz Tanıma ve Duygu Analizi Sistemi"* projesinin üçüncü hafta çalışmalarını kapsamaktadır. İkinci haftada gerçekleştirilen teknoloji seçimi ve kavramsal analiz süreçlerinin ardından, bu hafta projenin **"Tasarım ve Mimari Yapılandırma"** evresine geçiş yapılmıştır.

Üçüncü hafta çalışmalarının temel odağı; sistemin modülleri arasındaki veri akışını standardize etmek, veritabanı ilişkilerini kurgulamak ve algoritma mantığını matematiksel/mantıksal düzlemde doğrulamaktır. Tasarım evresinde alınan kararlar, projenin gerçek zamanlı çalışma performansını ve sistem güvenliğini doğrudan etkileyecek temel yapı taşlarını oluşturmaktadır.

---

# 2. HAFTALIK ODAK NOKTASI VE HEDEFLER

Hafta 3 kapsamında ekip olarak aşağıdaki teknik hedeflere odaklanılmıştır:

## * Sistem Mimarisi
* Görüntü işleme hattının (*pipeline*) katmanlı bir yapıda tasarlanması  
* YuNet/KCF entegrasyonunun planlanması  

## * Veri Yönetimi
* PostgreSQL üzerinde analiz sonuçlarının ve kullanıcı bilgilerinin saklanması  
* Tutarlı bir ilişkisel veritabanı şemasının oluşturulması  

## * API ve Haberleşme
* Modüller arası veri transferi için API uç noktalarının planlanması  
* JWT tabanlı güvenlik mekanizmasının belirlenmesi  

## * Algoritma Optimizasyonu
* VGG-Face modeli üzerinden duygu analizi süreçlerinin iyileştirilmesi  
* Hata payını minimize edecek filtreleme tekniklerinin geliştirilmesi  

## * Kullanıcı Deneyimi
* Yönetim paneli için wireframe taslaklarının oluşturulması  
* Kullanıcı akış senaryolarının netleştirilmesi  

---

# 3. GÖREV DAĞILIMI VE SORUMLULUK MATRİSİ

Projenin bu aşamasında, her ekip üyesi kendi uzmanlık alanı doğrultusunda sistemin bir modülünün teknik tasarımından sorumlu tutulmuştur.

## * Piksel Mühendisleri Ekibi

| Sorumlu Üye            | Proje Rolü                                   | Hafta 3 Teknik Görev Tanımı                                                                 |
|-----------------------|----------------------------------------------|---------------------------------------------------------------------------------------------|
| Şeyma Nur Katar       | *Grup Yöneticisi / Veritabanı Mimarı*        | PostgreSQL veritabanı şemasının tasarımı, tablolar arası ilişkiler ve veri güvenliği planı |
| Hatice Kırmızıgül     | *Analiz Uzmanı / Görüntü İşleme Mimarı*      | YuNet ve KCF tabanlı yüz tanıma/takip mimarisi ve UML diyagramlarının oluşturulması        |
| Muhammed Taha Gökdere | *Analiz Uzmanı / Yapay Zeka Tasarımcısı*     | VGG-Face modeli ile duygu analizi algoritması ve filtreleme süreçlerinin tasarımı          |
| Eren Bilge Koçak      | *Yazılım Geliştirici / Entegrasyon Sorumlusu*| RESTful API, JWT güvenlik yapısı ve veri akış şeması                                        |
| Mehmet Berat Uygur    | *UI/UX Tasarımcısı / Arayüz Geliştirici*     | Yönetim paneli wireframe taslakları ve responsive tasarım planlaması                       |

---

# 4. SONUÇ

Hafta 3 sonunda elde edilen tüm tasarım dökümanları, birbirini teknik olarak destekleyecek şekilde entegre edilmiştir. Bu rapor; veritabanından kullanıcı arayüzüne, yapay zeka modelinden API katmanına kadar sistemin tüm iskeletini tanımlamaktadır.

Belirlenen bu mimari çerçeve, dördüncü haftada başlayacak olan uygulama ve kodlama süreci için kesinleşmiş rehber niteliğindedir.

# YÜZ TANIMA VE DUYGU ANALİZİ SİSTEMİ  
## *3. HAFTA ANALİZ VE TASARIM DÖKÜMANTASYONU*

---

# 1. PROJE GENEL GİRİŞİ

Bu döküman, *"Yüz Tanıma ve Duygu Analizi Sistemi"* projesinin üçüncü hafta çalışmalarını kapsamaktadır. Analiz evresinden tasarım evresine geçiş yapılan bu aşamada; sistemin **yazılım mimarisi**, **modüler yapısı** ve **veritabanı şeması** detaylandırılmıştır.  

Projenin temel hedefi olan *gerçek zamanlı analiz yeteneğini* desteklemek amacıyla, veri saklama ve işleme süreçleri **en düşük gecikme süresini hedefleyecek şekilde** kurgulanmıştır.

Üçüncü hafta itibarıyla, sistemin *"Görüntü İşleme"* ve *"Veri Yönetimi"* katmanları arasındaki entegrasyon noktaları belirlenmiş; kullanılan algoritmaların (*YuNet, KCF*) üreteceği verilerin tutarlılığını sağlayacak ilişkisel model tasarlanmıştır.

---

# VERİTABANI ŞEMASI TASARIM RAPORU

## *Görev Tanımı:* Veritabanı Şeması Tasarımı ve Veri Yönetimi  
## *Proje Aşaması:* Tasarım ve Modelleme 
## *Hazırlayan:* Şeyma Nur Katar

---

# 1. VERİTABANI YÖNETİM SİSTEMİ (DBMS) SEÇİMİ

Sistemin tüm bileşenlerinden gelen verilerin **kalıcı, güvenli ve performanslı** bir şekilde saklanması için veritabanı yönetim sistemi olarak *PostgreSQL* tercih edilmiştir.

## *Seçim Gerekçeleri*

- *İlişkisel Veri Kararlılığı:* Kullanıcı, tespit ve analiz verileri arasındaki karmaşık ilişkilerin korunması  
- *JSONB Desteği:* Yapay zeka modellerinden gelen dinamik verilerin esnek şekilde saklanabilmesi  
- *Yüksek Yük Performansı:* Yoğun veri akışında güçlü indeksleme kabiliyeti  

---

# 2. VERİTABANI TABLO YAPILARI

Sistemin mimari tasarımıyla uyumlu olacak şekilde aşağıdaki tablolar tanımlanmıştır.

---

## *2.1 Tablo: users (Sistem Yetkilileri)*

Yönetim paneline erişim yetkisi bulunan kullanıcı bilgilerini tutar.

| Sütun Adı      | Veri Tipi   | Özellik            | Açıklama                          |
|----------------|------------|--------------------|----------------------------------|
| user_id        | Serial     | Primary Key        | Kullanıcı benzersiz kimliği      |
| username       | Varchar(50)| Unique, Not Null   | Sisteme giriş adı                |
| password_hash  | Text       | Not Null           | Bcrypt ile korunmuş şifre        |
| role           | Varchar(20)| Not Null           | Yetki düzeyi (Admin, Operatör)   |

---

## *2.2 Tablo: cameras (Donanım Kaynakları)*

Sisteme bağlı görüntü kaynaklarının konfigürasyonlarını saklar.

| Sütun Adı   | Veri Tipi    | Özellik      | Açıklama                     |
|-------------|-------------|--------------|------------------------------|
| camera_id   | Serial      | Primary Key  | Kamera benzersiz kimliği     |
| camera_name | Varchar(100)| Not Null     | Kamera lokasyon bilgisi      |
| stream_url  | Text        | Not Null     | RTSP veya donanım yolu       |

---

## *2.3 Tablo: detections (Yüz Tespit ve Takip Kayıtları)*

Yüz tespit (*YuNet*) ve takip (*KCF*) modüllerinden gelen verileri saklar.

| Sütun Adı        | Veri Tipi  | Özellik            | Açıklama                                |
|------------------|-----------|--------------------|------------------------------------------|
| detection_id     | BigSerial | Primary Key        | Tespit benzersiz kimliği                 |
| camera_id        | Integer   | Foreign Key        | Kaynak kamera                            |
| bounding_box     | JSONB     | Not Null           | Koordinatlar (x, y, w, h)                |
| confidence_score | Float     | Not Null           | Tespit doğruluk oranı                    |
| tracker_info     | Varchar(50)| Not Null          | Kullanılan takip algoritması             |
| timestamp        | Timestamp | Default Now()      | Kayıt zamanı                             |

---

## *2.4 Tablo: emotion_analysis (Analiz Sonuçları)*

Duygu analizi sonuçlarını tespit verileriyle ilişkilendirir.

| Sütun Adı     | Veri Tipi  | Özellik      | Açıklama                          |
|---------------|-----------|--------------|----------------------------------|
| analysis_id   | BigSerial | Primary Key  | Analiz kimliği                   |
| detection_id  | BigInt    | Foreign Key  | İlgili tespit verisi             |
| emotion_label | Varchar(20)| Not Null    | Tahmin edilen duygu              |
| score         | Float     | Not Null     | Güven skoru                      |

---

# 3. MİMARİ ENTEGRASYON VE VERİ İLİŞKİLERİ

Sistem tasarımı, veri bütünlüğünü korumak amacıyla **ilişkisel model** üzerine kurulmuştur:

- *Kamera → Tespit:* Bir kamera birden fazla tespit üretebilir *(1:N)*  
- *Tespit → Analiz:* Her tespit bir veya daha fazla analiz sonucu ile ilişkilendirilebilir *(1:1 / 1:N)*  

---

# 4. PERFORMANS OPTİMİZASYONU VE İNDEKSLEME

Sistemin düşük gecikme ile çalışabilmesi için aşağıdaki stratejiler uygulanmıştır:

- *Zaman Bazlı İndeksleme:* `timestamp` alanına **B-Tree index** atanmıştır  
- *Kısmi İndeksleme:* `confidence_score` üzerinden filtrelenmiş sorgular optimize edilmiştir  

---

# 5. VERİ GÜVENLİĞİ VE ERİŞİM KONTROLÜ

- *Şifreleme:* Kullanıcı şifreleri **Bcrypt** ile hashlenir  
- *API İzolasyonu:* Tüm veri erişimi kimlik doğrulamalı API üzerinden yapılır  
- *Veri Bütünlüğü:* FOREIGN KEY ve CASCADE yapıları ile referans bütünlüğü korunur  

---


# YÜZ TANIMA VE TAKİP MODÜLÜ MİMARİ TASARIM RAPORU

## *Görev Tanımı:* Yüz Tanıma ve Takip Modülü Analizi ve Tasarımı  
## *Proje Aşaması:* Tasarım ve Modelleme  
## *Hazırlayan:* Hatice Kırmızıgül
---

# 1. AMAÇ VE KAPSAM

Bu rapor, *OpenCV* kütüphanesi kullanılarak gerçek zamanlı video akışından yüzleri tespit eden ve takip eden modülün yazılım mimarisini tanımlar.  

Tasarım sürecinde aşağıdaki kriterler temel alınmıştır:

- *Düşük gecikme süresi*  
- *Değişken aydınlatma koşullarına dayanıklılık*  
- *Farklı yüz açılarını destekleme*  
- *Ölçeklenebilir performans*  

---

# 2. SİSTEM MİMARİSİ

Modül, sorumlulukların ayrıştırılması ilkesine uygun olarak **katmanlı mimari** ile tasarlanmıştır:

## * Katmanlar

- *Video Capture Layer:* Kamera donanımından ham karelerin alınması  
- *Preprocessing Layer:* Gürültü azaltma, histogram eşitleme, yeniden boyutlandırma  
- *Face Detection Layer:* İlk yüz tespitinin gerçekleştirilmesi  
- *Face Tracking Layer:* Yüzün ardışık karelerde takibi  
- *Decision Layer:* Kimlik doğrulama, alarm ve veri kayıt süreçleri  

---

# 3. NESNE TABANLI TASARIM VE SINIF SORUMLULUKLARI

Sistemin sürdürülebilirliği için önerilen sınıf yapıları aşağıdadır:

| Sınıf Adı           | Temel Fonksiyonlar                         | Sorumluluk                                      |
|---------------------|--------------------------------------------|-------------------------------------------------|
| VideoStreamManager  | startStream(), readFrame(), stopStream()   | Kamera akış yönetimi ve veri yakalama           |
| Preprocessor        | resizeFrame(), normalizeLighting(), denoise() | Görüntü iyileştirme ve normalizasyon        |
| FaceDetector        | detectFaces()                              | Yüz tespiti ve koordinat üretimi                |
| FaceTracker         | initTracker(), updateTracker()             | Nesne takibi sürekliliği                        |
| PerformanceMonitor  | calculateFPS(), logLatency()               | Performans ve kaynak izleme                     |

---

# 4. SİSTEM AKTİVİTE AKIŞI

Sistemin operasyonel akışı aşağıdaki gibidir:

1. Sistem başlatılır ve kamera aktive edilir  
2. Anlık kare okunur ve ön işleme aktarılır  
3. Yüz tespiti algoritması çalıştırılır  
4. Takip mekanizması başlatılır veya güncellenir  
5. Sonuçlar görselleştirilir ve döngü devam eder  

---

# 5. ALGORİTMALARIN KARŞILAŞTIRMALI ANALİZİ

| Yaklaşım                     | Avantajları                                 | Dezavantajları                                  |
|-----------------------------|----------------------------------------------|-------------------------------------------------|
| Haar Cascade                | Yüksek hız, düşük CPU kullanımı              | Işık ve açı değişimlerine duyarlılık            |
| HOG + SVM                   | Daha kararlı yapı                            | Yüksek çözünürlükte performans düşüşü           |
| CNN Tabanlı (YuNet / SSD)   | Yüksek doğruluk ve dayanıklılık              | Donanım bağımlılığı (GPU) ihtiyacı olabilir     |

---

# 6. SEÇİLEN ALGORİTMALAR VE TEKNİK GEREKÇELER

Proje kapsamında *OpenCV DNN tabanlı YuNet* veya hafif CNN modelleri tercih edilmiştir.

## * Gerekçeler

- *Kararlılık:* Düşük ışıkta daha iyi performans  
- *Açı Dayanımı:* Profil ve eğik yüzlerde yüksek başarı  
- *Entegrasyon:* OpenCV ile optimize uyum  

---

# 7. NESNE TAKİP STRATEJİSİ

Yüz takibi için *KCF (Kernelized Correlation Filters)* algoritması seçilmiştir.

## * Özellikler

- *Yüksek hız:* Gerçek zamanlı kullanım için uygun  
- *Esneklik:* Gerektiğinde *CSRT* algoritmasına geçiş imkanı  

---

# 8. ÇEVRESEL KOŞULLAR VE OPTİMİZASYON

## * Optimizasyon Teknikleri

- *Aydınlatma:* CLAHE uygulanması  
- *Açı Kontrolü:* >30° açılarda CNN avantajı kullanımı  
- *Arka Işık:* Gamma Correction uygulanması  

---

# 9. PERFORMANS VE KAYNAK YÖNETİMİ

Sistem performansını artırmak için:

- *Frame Skipping:* N karede bir tespit yapılması  
- *ROI Kullanımı:* Sadece ilgili bölgede analiz  
- *Threading:* Paralel video işleme  
- *Hafif Modeller:* INT8 / FP16 optimizasyonu  

---

# 10. OPERASYONEL İŞ AKIŞI ÖRNEĞİ

Kamera görüntüsü alınır → ön işleme uygulanır → CNN modeli ile yüz tespiti yapılır → *bounding box* elde edilir → takip modülüne aktarılır → sistem eş zamanlı olarak performans ölçümü yapar.

---

# 11. SEKANSIYEL VERİ AKIŞI

## * Veri Akışı

- Camera → VideoStreamManager  
- VideoStreamManager → Preprocessor  
- Preprocessor → FaceDetector  
- FaceDetector → FaceTracker  
- FaceTracker → UI  

---

# 12. SONUÇ

CNN tabanlı yüz tespit modeli ile *KCF* takip algoritmasının birlikte kullanımı; **doğruluk, hız ve gerçek zamanlılık** arasında optimum denge sağlamaktadır.  

Tasarlanan mimari yapı, hem akademik standartlara hem de gerçek dünya uygulamalarına uygun, sürdürülebilir ve ölçeklenebilir bir çözüm sunmaktadır.


# DUYGU ANALİZİ ALGORİTMASI TASARIM RAPORU

## *Görev Tanımı:* Duygu Analizi Algoritma Tasarımı ve Optimizasyonu  
## *Proje Aşaması:* Tasarım ve Modelleme  
## *Hazırlayan:* Muhammed Taha Gökdere
---

# 1. DUYGU SPEKTRUMU: TESPİT PARAMETRELERİ

Sistem, insan psikolojisindeki *"7 Temel Duygu"* modelini baz almaktadır. Bu duygular, yüz kaslarındaki mikro hareketler üzerinden analiz edilir.

## * Duygu Kategorileri

### * Pozitif Duygular
- *Mutluluk:* Gülümseme ve göz kenarı kırışıklığı  

### * Negatif Duygular
- *Üzüntü:* Dudak kenarlarının aşağı sarkması  
- *Öfke:* Çatık kaşlar  
- *Korku:* Açık ağız ve gergin gözler  
- *Tiksinti:* Burun kırıştırma  

### * Dinamik / Anlık Duygular
- *Şaşkınlık:* Kalkık kaşlar ve açılmış ağız  

### * Referans Durumu
- *Nötr:* Kas aktivitesi olmayan temel durum  

---

# 2. MODEL KARŞILAŞTIRMASI VE STRATEJİK SEÇİM

Duygu analizi için farklı modeller karşılaştırılmıştır:

| Model             | Odak Noktası          | Uygunluk                                   | Karar   |
|------------------|----------------------|---------------------------------------------|---------|
| Google FaceNet   | Kimlik doğrulama     | Düşük (ifadeye değil geometriye odaklı)     | Elendi  |
| OpenFace         | Gerçek zamanlı hız   | Orta (düşük ışıkta hataya açık)             | Elendi  |
| VGG-Face         | Derin öznitelik      | Çok yüksek doğruluk                         | SEÇİLDİ |

## * Seçim Gerekçesi

Duygu analizi, yüzün kimliğinden ziyade *anlık ifadesine* odaklanır.  
*VGG-Face* modeli, çok katmanlı yapısı sayesinde yüz kaslarındaki küçük değişimleri yüksek doğrulukla yakalayabilmektedir.

---

# 3. ALGORİTMANIN ÇALIŞMA MİMARİSİ

Analiz süreci dört temel aşamadan oluşur:

## * 1. Yüz Yakalama ve Hizalama (Alignment)
- Kafa eğimi düzeltilir  
- Örneğin: 15° eğim dijital olarak normalize edilir  

## * 2. Işık Normalizasyonu
- Gölgeler yumuşatılır  
- Yanlış duygu tespiti engellenir  

## * 3. Vektör Analizi
- Yüz, binlerce matematiksel noktaya ayrılır  
- Noktalar arası ilişkiler hesaplanır  

## * 4. Olasılık Hesaplama (Softmax)
- Duygulara olasılık dağıtılır  
- Örnek: *%75 Mutlu, %20 Nötr, %5 Şaşkın*  

---

# 4. EĞİTİM VE İNCE AYAR (FINE-TUNING) PLANI

Model doğruluğunu artırmak için *Transfer Learning* uygulanacaktır.

## * Stratejiler

- *Özel Veri Seti:* FER-2013 gibi geniş veri setleri kullanımı  
- *Katman Dondurma:* İlk katmanlar sabit, son katmanlar eğitilir  
- *Learning Rate:* 0.0001 ile hassas öğrenme  

---

# 5. GÜVENLİRLİK VE FİLTRELEME TASARIMI

Hatalı sonuçları azaltmak için üç aşamalı kontrol mekanizması:

## * A. Zaman Pencereli Ortalama (Smoothing)
- Son 15 kare ortalaması alınır  
- Anlık değişimler filtrelenir  

## * B. Kararlılık Eşiği (Thresholding)
- Minimum %65 güven skoru şartı  
- Altı → *Nötr / Belirsiz*  

## * C. Ani Değişim Reddi (Hysteresis)
- Ani duygu sıçramaları engellenir  
- Önceki stabil durum korunur  

---

# 6. PERFORMANS BEKLENTİSİ

## * Sistem Performansı

- *Masaüstü / Sunucu:* 25–30 FPS (gerçek zamanlı)  
- *Mobil / Uç Cihaz:* 10–15 FPS  

## * Doğruluk Oranı

- İdeal koşullarda: *%88 – %92*  

---

# API ENTEGRASYONU VE VERİ AKIŞI TASARIM RAPORU

### *Görev Tanımı:* API Entegrasyonu Tasarımı ve Veri Akışı Yönetimi  
### *Proje Aşaması:* Tasarım ve Modelleme  
### *Hazırlayan:* Eren Bilge Koçak
---

## 1. GÖREV ÖZETİ VE KAPSAM

Bu çalışma kapsamında; yüz tanıma, takip ve duygu analizi modüllerinden gelen verileri merkezi bir yapıda toplayan, **RESTful prensiplerine uygun**, **yüksek güvenlikli** ve **ölçeklenebilir** bir API mimarisi tasarlanmıştır.  

Sistemin farklı platformlardan (*Python, C#, Java vb.*) erişilebilir olması sağlanmış ve performans optimizasyonları (*Caching*) devreye alınmıştır.

---

## 2. TEKNİK TASARIM VE GÜVENLİK MEKANİZMASI

Tasarlanan API mimarisinde aşağıdaki ileri seviye teknikler kullanılmıştır:

### * Kimlik Doğrulama ve Yetkilendirme (OAuth2 & JWT)
- Statik anahtarlar yerine *JWT (JSON Web Token)* kullanılmıştır  
- Kullanıcılar giriş yaparak *access token* alır  
- Tüm veri alışverişi bu token üzerinden güvenli şekilde gerçekleştirilir  

### * Modül Entegrasyonu
- Yüz tanıma, takip ve duygu verileri tek bir veri modelinde birleştirilmiştir  
- Ortak veri modeli: *AnalizSonucu (JSON)*  
- Veri bütünlüğü sağlanmıştır  

### * Ölçeklenebilirlik ve Önbellekleme (Caching)
- API önünde bir *cache katmanı* oluşturulmuştur  
- Tekrarlı istekler doğrudan bellekten karşılanır  
- Yapay zeka modüllerinin yükü azaltılır  

---

## 3. UYGULAMA VE TEST KANITLARI

### * A. API Güvenlik Katmanı (JWT Auth)

- Sistem yetkisiz erişimlere karşı korunmuştur  
- *Swagger UI* üzerinden OAuth2 ile test edilebilir yapı sağlanmıştır  
- Geliştiriciler için güvenli endpoint test ortamı sunulmuştur  
<img width="1900" height="268" alt="Ekran Resmi 2026-04-22 14 36 57" src="https://github.com/user-attachments/assets/9fd7e31b-b359-4b4f-b66e-df011d68c1a8" />

---

### * B. Entegre Veri Akışı ve 200 OK Yanıtı

Yüz, takip ve duygu verilerinin eş zamanlı olarak API üzerinden iletildiği ve sistemin başarılı şekilde yanıt verdiği doğrulanmıştır.

<img width="2894" height="1438" alt="Ekran Resmi 2026-04-22 14 37 42" src="https://github.com/user-attachments/assets/d9e70adf-ce61-4d73-a485-6110e040b0ac" />

#### * Örnek JSON Çıktısı

```json
{
  "kamera_id": 1,
  "tespit_id": 102,
  "kisi_adi": "Bilinmeyen",
  "duygu": "Mutlu",
  "koordinat": [150, 200, 50, 50],
  "guven_skoru": 0.94
}
```
### C. Performans ve Önbellekleme (Cache) Testi

Tekrarlı isteklerde sistemin önbellekten veri döndürdüğü doğrulanmıştır.

İşlem süresinde ciddi düşüş gözlemlenmiştir.

**Test çıktısı:** "Veri ÖNBELLEKTEN (Cache) hızlıca getirildi"
<img width="2940" height="429" alt="Ekran Resmi 2026-04-22 15 05 38" src="https://github.com/user-attachments/assets/65cfce22-81a7-4649-9797-7663738498e7" />

### D. Farklı Platformlardan Erişim (Client-Side Test)
API'nin farklı istemciler üzerinden erişilebilir olduğu doğrulanmıştır
Python ve diğer platformlardan başarılı bağlantı sağlanmıştır
JWT ile güvenli veri aktarımı gerçekleştirilmiştir
<img width="2215" height="255" alt="Ekran Resmi 2026-04-22 14 38 04" src="https://github.com/user-attachments/assets/9eed7bad-b262-4164-8255-4036a0a4e064" />

## 4. SONUÇ
Hafta 3 çalışmaları sonucunda; modüllerin entegre edildiği, yüksek güvenlikli ve performanslı bir API mimarisi başarıyla oluşturulmuştur.
Bu yapı, projenin web paneli, mobil uygulama ve diğer dış sistemlerle olan iletişiminin temelini oluşturmaktadır.

# WEB TABANLI YÖNETİM PANELİ ARAYÜZ TASARIM RAPORU

**Görev Tanımı:** Kullanıcı Arayüzü (UI) ve Deneyimi (UX) Tasarımı  
**Proje Aşaması:** Tasarım ve Modelleme  
**Hazırlayan:** Mehmet Berat Uygur
---

# 1. GİRİŞ

Bu çalışma kapsamında, sistemin yönetilmesi ve analiz sonuçlarının izlenmesi amacıyla Flask ve JavaScript teknolojileri üzerine kurgulanacak web tabanlı yönetim panelinin arayüz tasarımı oluşturulmuştur.

Tasarımın temel odak noktası; karmaşık analiz verilerinin anlaşılır bir şekilde görselleştirilmesi, sistem konfigürasyonlarının kolayca yönetilmesi ve raporlama süreçlerinin optimize edilmesidir.

---

## 2. TASARIM HEDEFLERİ VE PRENSİPLERİ

Sistemin arayüzü geliştirilirken aşağıdaki temel mühendislik ve tasarım hedefleri baz alınmıştır:

- **Sadelik ve Kullanılabilirlik:** Kullanıcıların minimum tıklama ile aradıkları bilgiye ulaşabilmesi için sezgisel bir yapı kurgulanmıştır.
- **Gerçek Zamanlı Veri Sunumu:** Yapay zeka modüllerinden gelen anlık yüz ve duygu verilerinin gecikmesiz bir şekilde ekrana yansıtılması sağlanmıştır.
- **Tutarlılık:** Tüm alt sayfalarda ve bileşenlerde standart renk paleti, tipografi ve ikon seti kullanımı benimsenmiştir.
- **Hızlı Geri Bildirim:** Kullanıcı işlemlerine sistemin verdiği yanıtların (hata, başarı, yüklenme durumu) açıkça belirtilmesi hedeflenmiştir.

---

## 3. HEDEF KULLANICI KİTLESİ VE ROLLER

Arayüz, sistemin farklı yetki seviyelerindeki kullanıcılar tarafından verimli kullanılmasına olanak tanıyacak şekilde tasarlanmıştır:

- **Sistem Yöneticileri:** Tam erişim, kullanıcı yönetimi ve algoritma parametre ayarları.
- **Güvenlik ve Operasyon Personeli:** Gerçek zamanlı izleme ve anlık bildirim takibi.
- **Analistler (İK ve Pazarlama):** Geçmişe dönük veriler üzerinden istatistiksel raporlama ve trend analizi.

---

## 4. ARAYÜZ BİLEŞENLERİ VE MODÜLLER

Yönetim paneli, işlevsel gereksinimlere göre beş ana modüle ayrılmıştır:

| Modül | İçerik ve İşlevler |
|------|---------------------|
| Dashboard (Ana Panel) | Canlı kamera akışı, anlık duygu dağılım grafikleri ve sistem sağlık göstergeleri |
| Kullanıcı Yönetimi | Personel ekleme/silme, yetkilendirme (RBAC) ve kullanıcı aktivite logları |
| Sistem Ayarları | Kamera kaynağı tanımlama, model hassasiyet ayarları ve bildirim konfigürasyonları |
| Raporlama Modülü | Tarih tabanlı filtreleme, analiz verilerinin dışa aktarımı (PDF/DOCX) |
| Görselleştirme Alanı | Çubuk, pasta ve çizgi grafikler ile veri analitiği |

---

## 5. WIREFRAME VE YERLEŞİM PLANI

Arayüzün mekansal yerleşimi modern web standartlarına uygun olarak üç ana bölüme ayrılmıştır:

- **Üst Navigasyon (Navbar):** Kurumsal logo, kullanıcı profil yönetimi ve sistem bildirim merkezi
- **Yan Menü (Sidebar):** Modüller arası hızlı geçişi sağlayan dikey navigasyon bloğu
- **İçerik Alanı (Main Content):** Dinamik verilerin, grafiklerin ve canlı kamera görüntülerinin yer aldığı alan

---

## 6. RESPONSIVE (DUYARLI) TASARIM STRATEJİSİ

Sistemin tüm cihazlarda erişilebilir olması için aşağıdaki stratejiler uygulanmıştır:

- **Esnek Grid Sistemi:** İçeriklerin ekran boyutuna göre yeniden konumlanması
- **Katlanabilir Menüler:** Mobil görünümde yan menünün gizlenmesi
- **Ölçeklenebilir Grafikler:** Chart.js grafiklerinin ekran boyutuna uyum sağlaması

---

## 7. KULLANILAN TEKNOLOJİ YIĞINI

Arayüz geliştirme sürecinde kullanılan teknolojiler:

- **Backend:** Flask (Python)
- **Frontend:** HTML5, CSS3, JavaScript (ES6+)
- **UI Framework:** Tailwind CSS / Bootstrap
- **Grafik Kütüphaneleri:** Chart.js / D3.js

---

## 8. SONUÇ

Tasarımı tamamlanan yönetim paneli arayüzü; kullanıcı deneyimini merkeze alan, teknik verileri anlaşılır kılan ve modern tasarım standartlarını karşılayan bir yapıda kurgulanmıştır.

Bu yapı, sistem yönetimini kolaylaştıracak ve yapay zeka modüllerinden gelen sonuçların stratejik bilgiye dönüşmesini sağlayacak güçlü bir arayüz temeli sunmaktadır.
