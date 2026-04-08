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


### 4. ÇALIŞAN SİSTEMİN KANITLARI VE TEST SONUÇLARI
A. API Kaynak Kodları (FastAPI Implementation)
<img width="1470" height="956" alt="Ekran Resmi 2026-04-09 00 07 52" src="https://github.com/user-attachments/assets/b0a2481a-4c34-4cdb-a6f1-3bb3c076b718" />

B. Test Sonuçları
Uvicorn Sunucusu: Yerel ortamda (localhost) başarıyla başlatıldı.

Swagger UI (HTTP 200): Yapılan entegrasyon testlerinde yetkili erişim sağlanmış ve sistem "200 OK" yanıtı ile başarılı veri aktarımını doğrulamıştır.

### 5. SONUÇ
Yüz tanıma ve duygu analizi motorunun dış dünya ile haberleşmesini sağlayacak olan REST API altyapısı, güvenli ve yüksek performanslı bir şekilde çalışır durumda teslim edilmiştir.
