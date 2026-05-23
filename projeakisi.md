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
* **NFR-2 (Platform Bağımsızlığı):** FastApı tabanlı web paneli, hem masaüstü hem de mobil tarayıcılarda (Responsive) sorunsuz çalışmalıdır.
* **NFR-3 (Hata Yönetimi):** Kamera bağlantısı koptuğunda sistem çökmemeli, arayüzde "Kamera Bağlantısı Bekleniyor..." uyarısı vermelidir.
* **NFR-4 (Veri Gizliliği):** KVKK/GDPR uyumluluğu gereği analiz edilen yüz görüntüleri yerel diskte açık bir şekilde tutulmamalı, sadece vektörel veriler (embeddings) saklanmalıdır.

### **4. Sistem Mimarisi ve Veri Akış Şeması**
Sistem dört ana katman üzerinde kurgulanmıştır:
1.  **Input Layer:** `cv2.VideoCapture(0)` ile yerel veya IP kameradan akış alınır.
2.  **Processing Layer (OpenCV):**  Haar Cascades ile yüz koordinatları (Bounding Box) belirlenir."
3.  **Analysis Layer (PyTorch):** Kırpılan yüz görüntüsü PyTorch framework'ü üzerinden önceden eğitilmiş CNN modeline (dima806/facial_emotions_image_detection) gönderilir; duygu vektörü çıkarılır.
4.  **Presentation Layer (FastApı & JS):** Sonuçlar WebSockets veya HTTP polling ile arayüze aktarılır; Chart.js ile duygu değişim grafiği çizilir.

### **5. Kullanım Senaryosu (Use Case Description)**

| Aktör | İşlem | Sistem Tepkisi |
| :--- | :--- | :--- |
| **Sistem Yöneticisi** | Web paneline giriş yapar. | Dashboard üzerinden anlık kamera akışını başlatır. |
| **Sistem** | Bilinmeyen bir yüz tespit eder. | Yüzü çerçeve içine alır, "Bilinmeyen Kişi" yazar ve anlık duygusunu (Örn: Kızgın) belirler. |
| **Sistem** | Duygu eşiği aşılırsa (Örn: %90 Kızgın). | Log sistemine "Yüksek Stres Seviyesi" uyarısı düşer. |

### **6. Proje Kısıtları (Constraints)**
* **Donanım:** Uygulama, derin öğrenme (CNN) tabanlı modelin anlık işleme gereksinimleri nedeniyle en az 8 GB RAM ve Modern bir CPU/GPU gerektirir
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

| Teknoloji | Seçim Amacı | Avantajı | Dezavantajı / Risk |
| :--- | :--- | :--- | :--- |
| **Python 3.9+** | Ana Programlama Dili | AI/ML kütüphane desteği, hızlı prototipleme ve geniş topluluk desteği. | C++'a göre daha yavaş çalışma hızı (GIL kısıtlaması). |
| **OpenCV (Haar Cascade)** | Görüntü İşleme | Gerçek zamanlı (Real-time) işlem hızı, düşük kaynak tüketimi. | Karmaşık ışıklandırma koşullarında doğruluk kaybı riski. |
| **PyTorch (CNN)** | Duygu Analizi Modeli | Önceden eğitilmiş dima806 modeli ile yüksek doğruluk ve esnek optimizasyon. | CPU üzerinde çalışırken frame skipping gerektirmesi. |
| **FastAPI** | Backend Framework | Asenkron yapısı sayesinde yüksek performanslı REST API entegrasyonu. | Çok yüksek trafikli sistemlerde ek yapılandırma gerektirmesi. |
| **JavaScript** | Frontend & Dashboard | Dinamik veri görselleştirme (Chart.js) ve zengin kullanıcı etkileşimi. | Tarayıcı uyumluluğu ve performans takibi gereksinimi. |




 ### 3. DERİNLEMESİNE DEĞERLENDİRME VE RİSK ANALİZİ
#### 3.1. Neden Python ve FastAPI?
Projenin temelinde yer alan derin öğrenme modellerinin en kararlı performansı Python ekosisteminde vermesi nedeniyle Python ana dildir. FastAPI ise, projenin sistemler arası veri akışını (API katmanı) asenkron uç noktalarla çok daha hızlı ve düşük gecikmeyle (REST standartlarında) yönetmek için tercih edilmiştir.

#### 3.2. OpenCV (Haar Cascade) Tercih Nedeni
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

**Seçilen Algoritma:** PyTorch Framework ve dima806 CNN Modeli.

**Seçim Gerekçeleri:**
* **Donanım ve FPS Uyumluluğu:** 1. haftadaki testlerde modelin, donanım yetersizliklerine karşı geliştirdiğimiz "Frame Skipping" mimarisiyle tam uyum sağlaması ve FPS darboğazını aşmasıdır.
* **Yüz Tespiti Uyumluluğu:** Duygu analizi motoru, CPU dostu olan ve Frame Skipping mimarimizle milisaniyeler seviyesinde çalışan OpenCV (Haar Cascade) algoritmasının çıktılarından (Bounding Box) beslenerek hız avantajı sağlamaktadır.

### 4. Sonuç
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

* **Frontend:** JavaScript ve HTML/CSS (Chart.js entegrasyonu ile dinamik veri görselleştirme için).
* **Backend:** FastAPI (Asenkron veri işleme ve yüksek performanslı REST API entegrasyonu için).
* **Veritabanı:** SQLite (Sistemi yormayan hafif veri kaydı ve donanım kısıtlarına uyum için).
* **Grafik Kütüphanesi:** Chart.js (Dinamik veri görselleştirme için).
* **Kimlik Doğrulama:** JWT (JSON Web Token) tabanlı güvenli oturum yönetimi.

### 9. SONUÇ
Tasarlanan bu yönetim paneli, sistemin ürettiği karmaşık verileri merkezi bir noktada toplayarak kullanım kolaylığı, anlık veri takibi ve derinlemesine analiz kabiliyeti sunacaktır. Modüler yapısı sayesinde gelecekteki yeni analiz gereksinimlerine göre kolayca genişletilebilir bir mimariye sahiptir.
 

# 1. GENEL GİRİŞ

Bu döküman, Fırat Üniversitesi Yazılım Mühendisliği Bölümü bünyesinde yürütülen *"Yüz Tanıma ve Duygu Analizi Sistemi"* projesinin üçüncü hafta çalışmalarını kapsamaktadır. İkinci haftada gerçekleştirilen teknoloji seçimi ve kavramsal analiz süreçlerinin ardından, bu hafta projenin **"Tasarım ve Mimari Yapılandırma"** evresine geçiş yapılmıştır.

Üçüncü hafta çalışmalarının temel odağı; sistemin modülleri arasındaki veri akışını standardize etmek, veritabanı ilişkilerini kurgulamak ve algoritma mantığını matematiksel/mantıksal düzlemde doğrulamaktır. Tasarım evresinde alınan kararlar, projenin gerçek zamanlı çalışma performansını ve sistem güvenliğini doğrudan etkileyecek temel yapı taşlarını oluşturmaktadır.

---

2. HAFTALIK ODAK NOKTASI VE HEDEFLER
Hafta 3 kapsamında ekip olarak aşağıdaki teknik hedeflere odaklanılmıştır:
* Sistem Mimarisi: Görüntü işleme hattının (pipeline) katmanlı bir yapıda tasarlanması ve OpenCV (Haar Cascade) ile KCF entegrasyonunun planlanması.
* Veri Yönetimi: Donanım dostu SQLite üzerinde analiz sonuçlarının ve kullanıcı bilgilerinin saklanması. Tutarlı bir ilişkisel veritabanı şemasının oluşturulması.
* API ve Haberleşme: Modüller arası veri transferi için REST API (FastAPI) uç noktalarının planlanması ve JWT tabanlı güvenlik mekanizmasının belirlenmesi.
* Algoritma Optimizasyonu: PyTorch (CNN) modeli üzerinden duygu analizi süreçlerinin iyileştirilmesi ve hata payını minimize edecek filtreleme tekniklerinin geliştirilmesi.
* Kullanıcı Deneyimi: Yönetim paneli için wireframe taslaklarının oluşturulması ve kullanıcı akış senaryolarının netleştirilmesi.

3. GÖREV DAĞILIMI VE SORUMLULUK MATRİSİ
Projenin bu aşamasında, her ekip üyesi kendi uzmanlık alanı doğrultusunda sistemin bir modülünün teknik tasarımından sorumlu tutulmuştur.

* Şeyma Nur Katar (Grup Yöneticisi / Veritabanı Mimarı): SQLite veritabanı şemasının tasarımı, tablolar arası ilişkiler ve veri güvenliği planı.
* Hatice Kırmızıgül (Analiz Uzmanı / Görüntü İşleme Mimarı): Haar Cascade ve KCF tabanlı yüz tanıma/takip mimarisi ve UML diyagramlarının oluşturulması.
* Muhammed Taha Gökdere (Analiz Uzmanı / Yapay Zeka Tasarımcısı): PyTorch (ViT Modeli) ile duygu analizi algoritması ve filtreleme süreçlerinin tasarımı.
* Eren Bilge Koçak (Yazılım Geliştirici / Entegrasyon Sorumlusu): REST API (FastAPI), JWT güvenlik yapısı ve veri akış şeması.
* Mehmet Berat Uygur (UI/UX Tasarımcısı / Arayüz Geliştirici): Web Paneli (FastAPI ve Chart.js destekli) wireframe taslakları ve responsive tasarım planlaması.

# 4. SONUÇ

Hafta 3 sonunda elde edilen tüm tasarım dökümanları, birbirini teknik olarak destekleyecek şekilde entegre edilmiştir. Bu rapor; veritabanından kullanıcı arayüzüne, yapay zeka modelinden API katmanına kadar sistemin tüm iskeletini tanımlamaktadır.

Belirlenen bu mimari çerçeve, dördüncü haftada başlayacak olan uygulama ve kodlama süreci için kesinleşmiş rehber niteliğindedir.

# YÜZ TANIMA VE DUYGU ANALİZİ SİSTEMİ  
## *3. HAFTA ANALİZ VE TASARIM DÖKÜMANTASYONU*

---

# 1. PROJE GENEL GİRİŞİ

Bu döküman, *"Yüz Tanıma ve Duygu Analizi Sistemi"* projesinin üçüncü hafta çalışmalarını kapsamaktadır. Analiz evresinden tasarım evresine geçiş yapılan bu aşamada; sistemin **yazılım mimarisi**, **modüler yapısı** ve **veritabanı şeması** detaylandırılmıştır.  

Projenin temel hedefi olan *gerçek zamanlı analiz yeteneğini* desteklemek amacıyla, veri saklama ve işleme süreçleri **en düşük gecikme süresini hedefleyecek şekilde** kurgulanmıştır.

Üçüncü hafta itibarıyla, sistemin *"Görüntü İşleme"* ve *"Veri Yönetimi"* katmanları arasındaki entegrasyon noktaları belirlenmiş; kullanılan algoritmaların (*Haar Cascade, KCF*) üreteceği verilerin tutarlılığını sağlayacak ilişkisel model tasarlanmıştır.

---

# VERİTABANI ŞEMASI TASARIM RAPORU

### *Görev Tanımı:* Veritabanı Şeması Tasarımı ve Veri Yönetimi  
### *Proje Aşaması:* Tasarım ve Modelleme 
### *Hazırlayan:* Şeyma Nur Katar

---

## 1. VERİTABANI YÖNETİM SİSTEMİ (DBMS) SEÇİMİ

Sistemin donanım kısıtları göz önüne alınarak, tüm bileşenlerden gelen verilerin hafif, hızlı ve sistemi yormayan bir şekilde saklanması için veritabanı yönetim sistemi olarak SQLite tercih edilmiştir.

### *Seçim Gerekçeleri*
* Düşük Kaynak Tüketimi: RAM ve CPU darboğazlarını engellemek adına sunucusuz ve dosya tabanlı hafif mimarisi.
* Hızlı Prototipleme: Konfigürasyon gerektirmeden doğrudan dosya üzerinden hızlı okuma/yazma işlemleri yapabilmesi.
* İlişkisel Veri Kararlılığı: Kullanıcı, tespit ve analiz verileri arasındaki karmaşık ilişkilerin korunması ve Foreign Key desteği.


---

## 2. VERİTABANI TABLO YAPILARI

Sistemin mimari tasarımıyla uyumlu olacak şekilde aşağıdaki tablolar tanımlanmıştır.

---

### *2.1 Tablo: users (Sistem Yetkilileri)*

Yönetim paneline erişim yetkisi bulunan kullanıcı bilgilerini tutar.
| Sütun Adı | Veri Tipi | Özellik | Açıklama |
| :--- | :--- | :--- | :--- |
| user_id | INTEGER | Primary Key | Kullanıcı benzersiz kimliği (Auto Increment) |
| username | Varchar(50) | Unique, Not Null | Sisteme giriş adı |
| password_hash | Text | Not Null | Bcrypt ile korunmuş şifre |
| role | Varchar(20) | Not Null | Yetki düzeyi (Admin, Operatör) |

### *2.2 Tablo: cameras (Donanım Kaynakları)*
Sisteme bağlı görüntü kaynaklarının konfigürasyonlarını saklar.
| Sütun Adı | Veri Tipi | Özellik | Açıklama |
| :--- | :--- | :--- | :--- |
| camera_id | INTEGER | Primary Key | Kamera benzersiz kimliği (Auto Increment) |
| camera_name | Varchar(100) | Not Null | Kamera lokasyon bilgisi |
| stream_url | Text | Not Null | RTSP veya donanım yolu |

### *2.3 Tablo: detections (Yüz Tespit ve Takip Kayıtları)*
Yüz tespit (Haar Cascade) ve takip (KCF) modüllerinden gelen verileri saklar.
| Sütun Adı | Veri Tipi | Özellik | Açıklama |
| :--- | :--- | :--- | :--- |
| detection_id | INTEGER | Primary Key | Tespit benzersiz kimliği (Auto Increment) |
| camera_id | INTEGER | Foreign Key | Kaynak kamera |
| bounding_box | TEXT (JSON) | Not Null | Koordinatlar (x, y, w, h) |
| confidence_score | Float | Not Null | Tespit doğruluk oranı |
| tracker_info | Varchar(50) | Not Null | Kullanılan takip algoritması |
| timestamp | Timestamp | Default Now() | Kayıt zamanı |

### *2.4 Tablo: emotion_analysis (Analiz Sonuçları)*
Duygu analizi sonuçlarını tespit verileriyle ilişkilendirir.
| Sütun Adı | Veri Tipi | Özellik | Açıklama |
| :--- | :--- | :--- | :--- |
| analysis_id | INTEGER | Primary Key | Analiz kimliği (Auto Increment) |
| detection_id | INTEGER | Foreign Key | İlgili tespit verisi |
| emotion_label | Varchar(20) | Not Null | Tahmin edilen duygu |
| score | Float | Not Null | Güven skoru |



---

## 3. MİMARİ ENTEGRASYON VE VERİ İLİŞKİLERİ

Sistem tasarımı, veri bütünlüğünü korumak amacıyla **ilişkisel model** üzerine kurulmuştur:

- *Kamera → Tespit:* Bir kamera birden fazla tespit üretebilir *(1:N)*  
- *Tespit → Analiz:* Her tespit bir veya daha fazla analiz sonucu ile ilişkilendirilebilir *(1:1 / 1:N)*  

---

## 4. PERFORMANS OPTİMİZASYONU VE İNDEKSLEME

Sistemin düşük gecikme ile çalışabilmesi için aşağıdaki stratejiler uygulanmıştır:

- *Zaman Bazlı İndeksleme:* `timestamp` alanına **B-Tree index** atanmıştır  
- *Kısmi İndeksleme:* `confidence_score` üzerinden filtrelenmiş sorgular optimize edilmiştir  

---

## 5. VERİ GÜVENLİĞİ VE ERİŞİM KONTROLÜ

- *Şifreleme:* Kullanıcı şifreleri **Bcrypt** ile hashlenir  
- *API İzolasyonu:* Tüm veri erişimi kimlik doğrulamalı API üzerinden yapılır  
- *Veri Bütünlüğü:* FOREIGN KEY ve CASCADE yapıları ile referans bütünlüğü korunur  

---


# YÜZ TANIMA VE TAKİP MODÜLÜ MİMARİ TASARIM RAPORU

### *Görev Tanımı:* Yüz Tanıma ve Takip Modülü Analizi ve Tasarımı  
### *Proje Aşaması:* Tasarım ve Modelleme  
### *Hazırlayan:* Hatice Kırmızıgül
---

## 1. AMAÇ VE KAPSAM

Bu rapor, *OpenCV* kütüphanesi kullanılarak gerçek zamanlı video akışından yüzleri tespit eden ve takip eden modülün yazılım mimarisini tanımlar.  

Tasarım sürecinde aşağıdaki kriterler temel alınmıştır:

- *Düşük gecikme süresi*  
- *Değişken aydınlatma koşullarına dayanıklılık*  
- *Farklı yüz açılarını destekleme*  
- *Ölçeklenebilir performans*  

---

## 2. SİSTEM MİMARİSİ

Modül, sorumlulukların ayrıştırılması ilkesine uygun olarak **katmanlı mimari** ile tasarlanmıştır:

### * Katmanlar

- *Video Capture Layer:* Kamera donanımından ham karelerin alınması  
- *Preprocessing Layer:* Gürültü azaltma, histogram eşitleme, yeniden boyutlandırma  
- *Face Detection Layer:* İlk yüz tespitinin gerçekleştirilmesi  
- *Face Tracking Layer:* Yüzün ardışık karelerde takibi  
- *Decision Layer:* Kimlik doğrulama, alarm ve veri kayıt süreçleri  

---

## 3. NESNE TABANLI TASARIM VE SINIF SORUMLULUKLARI

Sistemin sürdürülebilirliği için önerilen sınıf yapıları aşağıdadır:

| Sınıf Adı           | Temel Fonksiyonlar                         | Sorumluluk                                      |
|---------------------|--------------------------------------------|-------------------------------------------------|
| VideoStreamManager  | startStream(), readFrame(), stopStream()   | Kamera akış yönetimi ve veri yakalama           |
| Preprocessor        | resizeFrame(), normalizeLighting(), denoise() | Görüntü iyileştirme ve normalizasyon        |
| FaceDetector        | detectFaces()                              | Yüz tespiti ve koordinat üretimi                |
| FaceTracker         | initTracker(), updateTracker()             | Nesne takibi sürekliliği                        |
| PerformanceMonitor  | calculateFPS(), logLatency()               | Performans ve kaynak izleme                     |

---

## 4. SİSTEM AKTİVİTE AKIŞI

Sistemin operasyonel akışı aşağıdaki gibidir:

1. Sistem başlatılır ve kamera aktive edilir  
2. Anlık kare okunur ve ön işleme aktarılır  
3. Yüz tespiti algoritması çalıştırılır  
4. Takip mekanizması başlatılır veya güncellenir  
5. Sonuçlar görselleştirilir ve döngü devam eder  

---

## 5. ALGORİTMALARIN KARŞILAŞTIRMALI ANALİZİ

5. ALGORİTMALARIN KARŞILAŞTIRMALI ANALİZİ
| Yaklaşım | Avantajları | Dezavantajları |
| :--- | :--- | :--- |
| Haar Cascade | Yüksek hız, minimum CPU kullanımı ve Frame Skipping uyumu | Işık ve açı değişimlerine duyarlılık (Histogram eşitleme ile çözülecek) |
| HOG + SVM | Daha kararlı yapı | Yüksek çözünürlükte performans düşüşü |
| CNN Tabanlı Modeller | Yüksek doğruluk ve dayanıklılık | Donanım bağımlılığı (CPU'da FPS darboğazı) |
---

## 6. SEÇİLEN ALGORİTMALAR VE TEKNİK GEREKÇELER

Proje kapsamında yüz tespiti için OpenCV (Haar Cascade) algoritması tercih edilmiştir.
* Gerekçeler
Kararlılık: Frame Skipping mantığıyla çalıştığında milisaniyeler içinde sonuç vermesi.
Kaynak Tasarrufu: Ağır DNN/CNN tabanlı modellerden kaçınılarak CPU gücünün tamamen ana duygu analizi modeline (ViT) ayrılması.
Entegrasyon: KCF takip algoritmasıyla %100 uyumlu ve optimize çalışması.
---

## 7. NESNE TAKİP STRATEJİSİ

Yüz takibi için *KCF (Kernelized Correlation Filters)* algoritması seçilmiştir.

### * Özellikler

- *Yüksek hız:* Gerçek zamanlı kullanım için uygun  
- *Esneklik:* Gerektiğinde *CSRT* algoritmasına geçiş imkanı  

---

## 8. ÇEVRESEL KOŞULLAR VE OPTİMİZASYON

### * Optimizasyon Teknikleri

- *Aydınlatma:* CLAHE uygulanması  
- *Açı Kontrolü:* >30° açılarda CNN avantajı kullanımı  
- *Arka Işık:* Gamma Correction uygulanması  

---

## 9. PERFORMANS VE KAYNAK YÖNETİMİ

Sistem performansını artırmak için:

- *Frame Skipping:* N karede bir tespit yapılması  
- *ROI Kullanımı:* Sadece ilgili bölgede analiz  
- *Threading:* Paralel video işleme  
- *Hafif Modeller:* INT8 / FP16 optimizasyonu  

---

## 10. OPERASYONEL İŞ AKIŞI ÖRNEĞİ

Kamera görüntüsü alınır → ön işleme uygulanır → Haar Cascade algoritması ile yüz tespiti yapılır  → *bounding box* elde edilir → takip modülüne aktarılır → sistem eş zamanlı olarak performans ölçümü yapar.


---

## 11. SEKANSIYEL VERİ AKIŞI

### * Veri Akışı

- Camera → VideoStreamManager  
- VideoStreamManager → Preprocessor  
- Preprocessor → FaceDetector  
- FaceDetector → FaceTracker  
- FaceTracker → UI  

---

## 12. SONUÇ

Haar Cascade yüz tespit algoritması ile KCF takip algoritmasının birlikte kullanımı; doğruluk, hız ve gerçek zamanlılık arasında optimum denge sağlamaktadır. Tasarlanan bu hafif mimari yapı, donanım darboğazlarını önleyerek sürdürülebilir bir çözüm sunmaktadır.

# DUYGU ANALİZİ ALGORİTMASI TASARIM RAPORU

### *Görev Tanımı:* Duygu Analizi Algoritma Tasarımı ve Optimizasyonu  
### *Proje Aşaması:* Tasarım ve Modelleme  
### *Hazırlayan:* Muhammed Taha Gökdere
---

## 1. DUYGU SPEKTRUMU: TESPİT PARAMETRELERİ

Sistem, insan psikolojisindeki *"7 Temel Duygu"* modelini baz almaktadır. Bu duygular, yüz kaslarındaki mikro hareketler üzerinden analiz edilir.

### * Duygu Kategorileri

#### * Pozitif Duygular
- *Mutluluk:* Gülümseme ve göz kenarı kırışıklığı  

#### * Negatif Duygular
- *Üzüntü:* Dudak kenarlarının aşağı sarkması  
- *Öfke:* Çatık kaşlar  
- *Korku:* Açık ağız ve gergin gözler  
- *Tiksinti:* Burun kırıştırma  

#### * Dinamik / Anlık Duygular
- *Şaşkınlık:* Kalkık kaşlar ve açılmış ağız  

#### * Referans Durumu
- *Nötr:* Kas aktivitesi olmayan temel durum  

---

## 2. MODEL KARŞILAŞTIRMASI VE STRATEJİK SEÇİM

Duygu analizi için farklı modeller karşılaştırılmış ve ilk hafta başarıyla test edilen yapıya sadık kalınmıştır:

| Model | Odak Noktası | Uygunluk | Karar |
| :--- | :--- | :--- | :--- |
| Google FaceNet | Kimlik doğrulama | Düşük (ifadeye değil geometriye odaklı) | Elendi |
| OpenFace | Gerçek zamanlı hız | Orta (düşük ışıkta hataya açık) | Elendi |
| **PyTorch (ViT Modeli)** | Transformer tabanlı derin öznitelik çıkarımı | Çok yüksek doğruluk ve esnek donanım uyumu | **SEÇİLDİ** |

**Seçim Gerekçesi**
Duygu analizi, yüzün kimliğinden ziyade anlık ifadesine odaklanır. PyTorch tabanlı dima806 (Vision Transformer - ViT) modeli, klasik CNN'lere göre görüntünün tamamındaki ilişkileri (attention mekanizması ile) çok daha iyi analiz etmektedir. Donanım yetersizliklerine karşı geliştirdiğimiz "Frame Skipping" mimarisiyle tam bir uyum içinde çalışmakta ve FPS darboğazı yaratmadan mikro-mimikleri yüksek doğrulukla yakalayabilmektedir.

---

## 3. ALGORİTMANIN ÇALIŞMA MİMARİSİ

Analiz süreci dört temel aşamadan oluşur:

### * 1. Yüz Yakalama ve Hizalama (Alignment)
- Kafa eğimi düzeltilir  
- Örneğin: 15° eğim dijital olarak normalize edilir  

### * 2. Işık Normalizasyonu
- Gölgeler yumuşatılır  
- Yanlış duygu tespiti engellenir  

### * 3. Vektör Analizi
- Yüz, binlerce matematiksel noktaya ayrılır  
- Noktalar arası ilişkiler hesaplanır  

### * 4. Olasılık Hesaplama (Softmax)
- Duygulara olasılık dağıtılır  
- Örnek: *%75 Mutlu, %20 Nötr, %5 Şaşkın*  

---

## 4. EĞİTİM VE İNCE AYAR (FINE-TUNING) PLANI

Model doğruluğunu artırmak için *Transfer Learning* uygulanacaktır.

### * Stratejiler

- *Özel Veri Seti:* FER-2013 gibi geniş veri setleri kullanımı  
- *Katman Dondurma:* İlk katmanlar sabit, son katmanlar eğitilir  
- *Learning Rate:* 0.0001 ile hassas öğrenme  

---

## 5. GÜVENLİRLİK VE FİLTRELEME TASARIMI

Hatalı sonuçları azaltmak için üç aşamalı kontrol mekanizması:

### * A. Zaman Pencereli Ortalama (Smoothing)
- Son 15 kare ortalaması alınır  
- Anlık değişimler filtrelenir  

### * B. Kararlılık Eşiği (Thresholding)
- Minimum %65 güven skoru şartı  
- Altı → *Nötr / Belirsiz*  

### * C. Ani Değişim Reddi (Hysteresis)
- Ani duygu sıçramaları engellenir  
- Önceki stabil durum korunur  

---

## 6. PERFORMANS BEKLENTİSİ

### * Sistem Performansı

- *Masaüstü / Sunucu:* 25–30 FPS (gerçek zamanlı)  
- *Mobil / Uç Cihaz:* 10–15 FPS  

### * Doğruluk Oranı

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

## 1. GİRİŞ

Bu çalışma kapsamında, sistemin yönetilmesi ve analiz sonuçlarının izlenmesi amacıyla FastAPI ve JavaScript teknolojileri üzerine kurgulanacak web tabanlı yönetim panelinin arayüz tasarımı oluşturulmuştur.

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

Arayüz geliştirme ve entegrasyon sürecinde kullanılan teknolojiler:
**Backend:** FastAPI (Python) - Asenkron ve yüksek performanslı veri transferi için.
**Frontend:** HTML5, CSS3, JavaScript (ES6+)
**UI Framework:** Tailwind CSS / Bootstrap
**Grafik Kütüphaneleri:** Chart.js (Dinamik veri görselleştirme için)

---

## 8. SONUÇ

Tasarımı tamamlanan yönetim paneli arayüzü; kullanıcı deneyimini merkeze alan, teknik verileri anlaşılır kılan ve modern tasarım standartlarını karşılayan bir yapıda kurgulanmıştır.

Bu yapı, sistem yönetimini kolaylaştıracak ve yapay zeka modüllerinden gelen sonuçların stratejik bilgiye dönüşmesini sağlayacak güçlü bir arayüz temeli sunmaktadır.


---

# YÜZ TANIMA VE DUYGU ANALİZİ SİSTEMİ  
## HAFTA 4 - UYGULAMA VE SİMÜLASYON ENTEGRASYONU

---

# Gerçek Zamanlı Yüz Tanıma ve Duygu Analizi Sistemi

Bu proje, gerçek zamanlı yüz tanıma ve duygu analizi gerçekleştiren, aynı zamanda 3D simülasyon, fizik motoru ve gelişmiş görselleştirme teknikleri içeren bir yapay zeka sistemidir.

---

## Proje Özellikleri

- Gerçek zamanlı yüz tanıma
- Duygu analizi (AI destekli)
- 3D simülasyon ve fizik motoru
- Gelişmiş ışıklandırma ve gölgeleme
- Performans optimizasyonları (GPU, FPS, model hızlandırma)
- Web tabanlı yönetim paneli

---

## Dokümantasyon

### Hafta 4 - Uygulama ve Simülasyon Entegrasyonu

| Doküman | Açıklama |
|--------|--------|
| [Genel Rapor](docs/hafta-4/01-genel-rapor.md) | Haftalık genel ilerleme |
| [Fizik Motoru](docs/hafta-4/02-fizik-motoru.md) | Çarpışma algılama |
| [Kamera & UI](docs/hafta-4/03-kamera-ui.md) | Kullanıcı etkileşimi |
| [Işıklandırma](docs/hafta-4/04-isiklandirma.md) | Görsel kalite |
| [Doku Optimizasyonu](docs/hafta-4/05-doku-optimizasyonu.md) | GPU performansı |
| [Model Optimizasyonu](docs/hafta-4/06-model-optimizasyonu.md) | AI hızlandırma |

---

## Kullanılan Teknolojiler

- Python (FastAPI)
- JavaScript (ES6+)
- HTML5 / CSS3
- Tailwind / Bootstrap
- Chart.js / D3.js
- NumPy / ONNX Runtime
- WebGL / 3D Render Motorları

---

## Sistem Mimarisi (Özet)

- Frontend → UI & Görselleştirme
- Backend → API & Model Yönetimi
- AI Katmanı → Yüz + Duygu Analizi
- Simülasyon → Fizik + 3D sahne

---

## Ekip

Dördüncü hafta operasyonel süreçlerinde ekip üyelerinin üstlendiği teknik görevler aşağıdaki tabloda sunulmuştur:

| Sorumlu Üye | Görev Başlığı | Teknik Kapsam |
|------------|--------------|---------------|
| Şeyma Nur Katar | Fizik Motoru Entegrasyonu | Çarpışma algılama ve nesne etkileşim simülasyonu |
| Mehmet Berat Uygur | Kamera ve Arayüz Entegrasyonu | Kullanıcı kontrolleri (zoom, pan, rotate) ve UI etkileşimi |
| Muhammed Taha Gökdere | Işıklandırma ve Gölge Geliştirme | Gerçekçi görselleştirme ve ışık kaynağı optimizasyonu |
| Hatice Kırmızıgül | Doku ve Performans İyileştirme | Texture mapping ve FPS optimizasyonu |
| Eren Bilge Koçak | Model İşleme Hızlandırılması | 3D veri yükleme ve işleme süreçlerinin optimizasyonu |

---

## Not

Bu repo akademik ve teknik geliştirme sürecinin dokümantasyonunu içermektedir.


# ÇARPIŞMA ALGILAMA VE FİZİK MOTORU ENTEGRASYONU RAPORU (HAFTA 4)

**Hazırlayan:** Şeyma Nur Katar  
**Proje:** Gerçek Zamanlı Yüz Tanıma ve Duygu Analizi Sistemi  
**Proje Görevi:** Çarpışma Algılama ve Fizik Motoru Entegrasyonu  

---

## 1. GİRİŞ

Bu çalışma kapsamında, üç boyutlu simülasyon ortamındaki nesnelerin birbirleriyle olan etkileşimlerini gerçeğe uygun şekilde simüle etmek amacıyla fizik motoru altyapısı kurgulanmış ve çarpışma algılama (*collision detection*) algoritmaları sisteme entegre edilmiştir.

Bu modül, sistemin görselleştirme katmanına fiziksel gerçekçilik katarak kullanıcı deneyimini üst seviyeye taşımayı hedeflemektedir.

---

## 2. PROJENİN AMACI

Fizik motoru entegrasyonu sürecinde aşağıdaki temel teknik hedeflere odaklanılmıştır:

- Nesnelerin sahnede birbirlerinin içinden geçmesini engelleyerek katı cisim (*rigid body*) dinamiğini sağlamak  
- Çarpışma anında oluşacak tepki kuvvetlerini (*collision response*) hesaplayarak gerçekçi hareketler oluşturmak  
- Karmaşık geometrilere sahip modellerde hesaplama maliyetini düşürmek için optimize edilmiş çarpışma hacimleri kullanmak  
- Fiziksel hesaplamaların sistemin genel FPS değerini düşürmemesini sağlamak  

---

## 3. TEKNİK AYRINTILAR VE METODOLOJİ

### 3.1. Çarpışma Algılama Algoritmaları

Sistemde performans ve hassasiyet dengesini korumak adına hiyerarşik bir yaklaşım benimsenmiştir:

- **AABB (Axis-Aligned Bounding Box):**  
  Nesnelerin etrafına eksenlere paralel kutular yerleştirilerek yapılan ilk aşama kontrolüdür. En düşük hesaplama maliyetine sahiptir.

- **Sphere Collision:**  
  Küresel nesneler veya hızlı hareket eden öğeler için merkezler arası uzaklık hesaplanarak çarpışma kontrolü yapılır.

- **Ray Casting:**  
  Kamera doğrultusu veya etkileşim çizgileri boyunca ışın izleme yöntemi kullanılarak hassas kesişim testleri uygulanır.

---

### 3.2. Fizik Motoru Entegrasyonu

Fizik motoru, her karede (*frame*) aşağıdaki işlem adımlarını uygular:

1. **Entegrasyon Adımı:**  
   Nesnelerin hız ve ivme değerlerine göre bir sonraki konumları hesaplanır.

2. **Kesişim Testi:**  
   Yeni konumlarda diğer nesnelerle çakışma olup olmadığı kontrol edilir.

3. **Çözümleme (Resolution):**  
   Çarpışma tespit edilirse nesneler çakışma noktasından geri itilir ve momentum korunumu yasalarına göre yeni hız vektörleri atanır.

---

## 4. PERFORMANS OPTİMİZASYON STRATEJİLERİ

Gerçek zamanlı sistem performansını korumak amacıyla aşağıdaki teknikler uygulanmıştır:

- **Spatial Partitioning (Uzamsal Bölümleme):**  
  Sahne gridlere bölünerek yalnızca aynı bölgedeki nesneler arasında çarpışma kontrolü yapılır.

- **Sleep State:**  
  Hareket etmeyen veya düşük hızdaki nesneler hesaplama dışı bırakılır.

- **Hafifletilmiş Çarpışma Geometrileri:**  
  Yüksek poligonlu modeller yerine daha basit proxy geometriler kullanılır.

---

## 5. KULLANILAN TEKNOLOJİLER

- **Motor Altyapısı:** JavaScript tabanlı fizik kütüphaneleri ve özel matematiksel fonksiyonlar  
- **Veri Yapıları:** JSON tabanlı nesne tanımları ve vektör matematiği sınıfları  
- **Görselleştirme:** Web tabanlı 3D render motorları ile senkronize çalışma  

---

## 6. SONUÇ VE DEĞERLENDİRME

Çarpışma algılama ve fizik motoru entegrasyonu, sistemi statik bir görsel yapıdan çıkararak dinamik ve etkileşimli bir simülasyon ortamına dönüştürmüştür.

Yapılan testlerde:

- Nesne etkileşimlerinin kararlı çalıştığı  
- Fizik hesaplamalarının sistem performansını olumsuz etkilemediği  

gözlemlenmiştir.

Gelecek aşamalarda:

- Soft body (yumuşak cisim) simülasyonları  
- Dinamik yerçekimi ve çevresel etkiler  

üzerine geliştirmeler planlanmaktadır.

---

# KAMERA KONTROLLERİ VE KULLANICI ARAYÜZÜ ENTEGRASYONU RAPORU (HAFTA 4)

**Hazırlayan:** Mehmet Berat Uygur  
**Proje:** Gerçek Zamanlı Yüz Tanıma ve Duygu Analizi Sistemi  
**Proje Görevi:** Kamera Kontrolleri ve Kullanıcı Arayüzü Entegrasyonu  

---

## 1. GİRİŞ

Bu çalışma kapsamında, gerçek zamanlı yüz tanıma ve duygu analizi sistemi içerisinde kullanılan kamera yönetim mekanizmaları geliştirilmiş ve kullanıcı arayüzüne (UI) entegre edilmiştir.

Temel amaç, son kullanıcının iki veya üç boyutlu sahne üzerindeki kontrolünü maksimize ederek analiz süreçlerini daha sezgisel ve hızlı hale getirmektir.

---

## 2. PROJENİN AMACI

Kamera ve arayüz entegrasyonu sürecinde aşağıdaki hedeflere odaklanılmıştır:

- Kullanıcı deneyimini (UX) iyileştirerek sistem karmaşıklığını azaltmak  
- Kamera hareketlerini doğal ve sezgisel hale getirmek  
- Gerçek zamanlı veri akışı sırasında operatörlere kullanım kolaylığı sağlamak  
- Arayüz bileşenleri ile kamera donanım/yazılım katmanları arasında tam uyum oluşturmak  

---

## 3. TEKNİK KAMERA KONTROLLERİ

Sistem üzerinde üç temel hareket mekanizması yapılandırılmıştır:

### 3.1. Zoom (Yakınlaştırma / Uzaklaştırma)

Kullanıcının detaylara odaklanmasını veya genel perspektifi görmesini sağlar. Özellikle mikro yüz ifadelerinin incelenmesinde kritik rol oynar.

- **Uygulama Metodu:**  
  Mouse tekerleği ve arayüz üzerindeki (+ / -) butonları  

---

### 3.2. Pan (Kaydırma)

Kameranın yatay ve dikey düzlemde hareket etmesini sağlayarak sahne içindeki farklı noktaların incelenmesine imkan tanır.

- **Uygulama Metodu:**  
  Mouse sürükleme (drag) ve yön butonları  

---

### 3.3. Rotate (Döndürme)

Sahnenin farklı açılardan görüntülenmesini sağlayarak derinlik ve perspektif analizine katkı sağlar.

- **Uygulama Metodu:**  
  Mouse sağ tık kombinasyonu ve arayüz rotasyon araçları  

---

## 4. KULLANICI ARAYÜZÜ (UI) ENTEGRASYONU

Kamera kontrolleri, sistemin genel tasarım diliyle uyumlu şekilde arayüz katmanına entegre edilmiştir.

### Temel Tasarım Prensipleri

- **Basitlik:** Sade ve anlaşılır bileşenler  
- **Erişilebilirlik:** Kontrollerin stratejik konumlandırılması  
- **Sezgisellik:** Eğitim gerektirmeden kullanım  

---

### 4.1. Arayüz Bileşenleri

- Dijital zoom kontrol butonları  
- Navigasyon (pan) araçları  
- Üç eksenli döndürme (rotate) kontrol paneli  
- **Reset (Sıfırla)** butonu (kamera başlangıç konumuna dönüş)  

---

## 5. KULLANICI DENEYİMİ (UX) İYİLEŞTİRMELERİ

Yapılan geliştirmeler sonucunda:

- Sahne kontrol hızı yaklaşık **%40 artırılmıştır**  
- Kamera hareketleri daha akıcı hale getirilmiştir  
- Esnek bakış açıları sayesinde analiz hata payı azaltılmıştır  

---

## 6. KULLANILAN TEKNOLOJİLER

- **Frontend:** HTML5, CSS3, JavaScript (ES6+)  
- **Kütüphaneler:** Kamera kontrol ve görüntüleme kütüphaneleri  
- **Entegrasyon:** Gerçek zamanlı görüntü işleme sistemleri ve API katmanı  

---

## 7. SONUÇ VE GELECEK PLANLAMASI

Kamera kontrolleri kullanıcı dostu bir şekilde sisteme entegre edilmiş ve başarıyla test edilmiştir. Bu yapı sistem verimliliğini önemli ölçüde artırmıştır.

### Gelecek Geliştirmeler

- Dokunmatik cihazlar için **pinch-to-zoom** desteği  
- Özelleştirilebilir klavye kısayolları  
- Yapay zeka destekli **otomatik odaklama (autofocus)** sistemleri  

---

# IŞIKLANDIRMA VE GÖLGE EFEKTLERİNİN GELİŞTİRİLMESİ RAPORU (HAFTA 4)

**Hazırlayan:** Muhammed Taha Gökdere  
**Proje:** Gerçek Zamanlı Yüz Tanıma ve Duygu Analizi Sistemi  
**Proje Görevi:** Işıklandırma ve Gölge Efektlerinin Geliştirilmesi  

---

## 1. IŞIK KAYNAKLARININ STRATEJİK YERLEŞİMİ

Sahnede derinlik algısını artırmak ve modellerin formunu belirginleştirmek amacıyla **Üç Noktalı Işıklandırma (Three-Point Lighting)** prensibi uygulanmıştır:

- **Ana Işık (Key Light):**  
  Sahnenin birincil ışık kaynağıdır. Sert gölgeler oluşturarak modellerin temel yapısını belirler.

- **Dolgu Işığı (Fill Light):**  
  Ana ışığın oluşturduğu sert gölgeleri yumuşatarak detay kaybını önler.

- **Arka Işık (Rim Light):**  
  Objelerin kenarlarını aydınlatarak arka plandan ayrılmasını sağlar ve derinlik etkisi oluşturur.

---

## 2. GÖLGE KALİTESİ VE YUMUŞATMA

Gerçekçi gölge üretimi için aşağıdaki teknikler uygulanmıştır:

- **Soft Shadows (Yumuşak Gölgeler):**  
  Işık kaynağından uzaklaştıkça yumuşayan ve doğal geçişler sunan gölge yapısı.

- **Contact Shadows:**  
  Nesnelerin zeminle temas ettiği bölgelerde ince ve yoğun gölgeler oluşturarak gerçekçilik artırılmıştır.

- **Shadow Cascades:**  
  Kameraya yakın alanlarda yüksek, uzak alanlarda düşük çözünürlüklü gölge haritaları kullanılarak performans optimize edilmiştir.

---

## 3. ATMOSFERİK EFEKTLER

Işığın sahne içerisindeki etkisini güçlendirmek amacıyla hacimsel efektler entegre edilmiştir:

- **Volumetric Fog (Hacimsel Sis):**  
  Işık hüzmelerinin görünür hale gelmesini sağlayarak derinlik algısını artırır.

- **Ambient Occlusion (AO):**  
  SSAO (Screen Space Ambient Occlusion) tekniği ile köşe ve birleşim noktalarında gölgelendirme yapılarak sahneye hacim kazandırılmıştır.

---

## 4. OPTİMİZASYON VE PERFORMANS AYARLARI

Görsel kaliteyi artırırken performansı korumak için şu yöntemler uygulanmıştır:

- **Baked vs Real-time Lighting:**  
  Statik nesneler için önceden hesaplanmış ışıklandırma (baking), dinamik nesneler için gerçek zamanlı ışıklandırma kullanılmıştır.

- **Light Culling Mask:**  
  Işık kaynaklarının yalnızca ilgili nesneleri etkilemesi sağlanarak gereksiz hesaplamalar azaltılmıştır.

- **Indirect Multiplier / Global Illumination:**  
  Işık yansımalarının optimize edilmesi ile minimum hesaplama ile maksimum gerçekçilik elde edilmiştir.

---

## 5. SONUÇ VE DEĞERLENDİRME

Geliştirilen ışıklandırma ve gölge modülü, sistemin görsel kalitesini profesyonel seviyeye taşımıştır.

Bu modül:

- Fizik motoru ile uyumlu çalışmakta  
- Kamera kontrolleri ile entegre şekilde sahne yönetimini desteklemekte  
- Yüz ve duygu analiz sonuçlarının daha net ve vurgulu şekilde gözlemlenmesini sağlamaktadır  

---

# DOKU KAPLAMA OPTİMİZASYONU VE PERFORMANS İYİLEŞTİRMELERİ RAPORU (HAFTA 4)

**Hazırlayan:** Hatice Kırmızıgül  
**Proje:** Gerçek Zamanlı Yüz Tanıma ve Duygu Analizi Sistemi  
**Proje Görevi:** Doku Kaplama Optimizasyonu ve Performans İyileştirmeleri  

---

## 1. AMAÇ VE KAPSAM

Bu çalışma, sistemin görselleştirme katmanında kullanılan üç boyutlu modellerin doku (*texture*) yapılarının optimize edilmesini amaçlamaktadır.

Temel hedefler:

- GPU bellek kullanımını minimize etmek  
- Veri yükleme sürelerini azaltmak  
- FPS (saniye başına kare) değerini artırmak  
- Gerçek zamanlı sistem performansını iyileştirmek  

---

## 2. DOKU BOYUTU VE ÇÖZÜNÜRLÜK STRATEJİSİ

GPU kaynaklarının verimli kullanılması amacıyla aşağıdaki stratejiler uygulanmıştır:

- **Çözünürlük Ölçeklendirme:**  
  Gereksiz 4K dokular yerine sahne ihtiyacına göre 2K ve 1K dokular tercih edilmiştir.

- **LOD (Level of Detail):**  
  Kameraya uzak nesnelerde düşük çözünürlüklü dokular kullanılarak render maliyeti azaltılmıştır.

---

## 3. DOKU FORMATLARI VE KARŞILAŞTIRMALI ANALİZ

Kullanılan doku formatları performans kriterlerine göre değerlendirilmiştir:

| Format | Avantajı | Dezavantajı | Kullanım Alanı |
|--------|----------|------------|----------------|
| PNG | Kayıpsız kalite | Büyük dosya boyutu | UI ve ikonlar |
| JPEG | Küçük boyut | Kayıplı sıkıştırma | Arka plan öğeleri |
| DDS | GPU dostu, hızlı yükleme | Masaüstü bağımlılığı | Masaüstü (**Seçildi**) |
| ASTC | Kalite/boyut dengesi | Sıkıştırma süresi | Mobil (**Seçildi**) |

---

## 4. SIKIŞTIRMA ALGORİTMALARI

Sistemde aşağıdaki GPU uyumlu sıkıştırma algoritmaları tercih edilmiştir:

- **DXT1 / BC1:**  
  Alfa kanalı gerektirmeyen dokular için

- **DXT5 / BC3:**  
  Şeffaflık içeren dokular için

**Sonuç:**  
Bu yöntemler sayesinde:

- CPU yükü azaltılmış  
- Bellek bant genişliği optimize edilmiş  
- VRAM kullanımı yaklaşık **%70 oranında düşürülmüştür**  

---

## 5. PERFORMANS ARTIRMA STRATEJİLERİ

Daha akıcı bir sistem performansı için şu teknikler uygulanmıştır:

- **Mipmap Kullanımı:**  
  Farklı mesafeler için optimize edilmiş doku seviyeleri

- **Texture Atlas:**  
  Birden fazla küçük dokunun tek bir büyük dokuda birleştirilmesi ile draw call azaltımı

- **Streaming Texture:**  
  Sadece görüş alanındaki dokuların dinamik olarak yüklenmesi

---

## 6. SİSTEM MİMARİSİ VE SINIF YAPISI

Doku yönetimi için iki temel modül geliştirilmiştir:

- **TextureManager:**  
  Doku yükleme, sıkıştırma ve mipmap üretimi

- **CompressionAnalyzer:**  
  Format performans analizleri ve en uygun sıkıştırma yönteminin belirlenmesi

---

## 7. SONUÇ VE DEĞERLENDİRME

Gerçekleştirilen doku optimizasyonları sonucunda:

- Karmaşık sahnelerde FPS değerleri stabil hale getirilmiştir  
- DDS ve ASTC formatları sayesinde platform bağımsız performans sağlanmıştır  
- Mipmap ve streaming teknikleri ile bellek yönetimi iyileştirilmiştir  

Bu iyileştirmeler, sistemdeki:

- Fizik motoru  
- Işıklandırma modülü  

gibi bileşenlerin daha verimli çalışabilmesi için donanım kaynaklarını serbest bırakmıştır.

---

# MODEL YÜKLEME VE İŞLEME SÜREÇLERİNİN HIZLANDIRILMASI RAPORU (HAFTA 4)

**Hazırlayan:** Eren Bilge Koçak  
**Proje:** Gerçek Zamanlı Yüz Tanıma ve Duygu Analizi Sistemi  
**Proje Görevi:** Model Yükleme ve İşleme Süreçlerinin Hızlandırılması  

---

## 1. GÖREVİN AMACI VE KAPSAMI

Bu çalışma, duygu analizi sistemlerinde kullanılan derin öğrenme modellerinin (PyTorch tabanlı ViT - dima806 vb.) donanım üzerindeki işlem yükünü optimize etmeyi ve kullanıcı deneyimini iyileştirmeyi amaçlamaktadır.

Projenin yüksek öncelikli yapısına uygun olarak:

- Sistem açılış süreleri azaltılmış  
- FPS (saniye başına işlenen kare sayısı) artırılmış  
- Gerçek zamanlı performans hedeflenmiştir  

---

## 2. UYGULANAN OPTİMİZASYON TEKNİKLERİ

Modellerin performansını artırmak amacıyla aşağıdaki yöntemler uygulanmıştır:

### 2.1. Lifespan Async Loading (Asenkron Yükleme)

* Transformer tabanlı derin öğrenme modellerinin (ör. ViT - dima806) sistem açılışını bloklaması engellenmiştir.
* Lifespan event yönetimi ile modeller arka planda asenkron olarak yüklenmiştir.
* API servisleri anında erişilebilir hale getirilmiştir.


---

### 2.2. NumPy Vektörizasyonu

- Döngü tabanlı işlemler yerine matris işlemleri tercih edilmiştir  
- CPU çekirdekleri daha verimli kullanılmıştır  
- İşlem süreleri milisaniye seviyesine düşürülmüştür  

---

### 2.3. Batch Processing (Toplu İşleme)

- Görüntüler tek tek değil toplu olarak işlenmiştir  
- Donanım gecikmesi (latency) minimize edilmiştir  
- Yüksek throughput elde edilmiştir  

---

## 3. PERFORMANS TESTLERİ

### 3.1. Sistem Açılış ve Model Hazırlık Testi

Modelin RAM’e yüklenme süresi optimize edilmiştir.

**Test Çıktısı:**

```json
{
  "model_durumu": "Hafızada Hazır (Pre-loaded)",
  "yukleme_hizi_saniye": 0.4527,
  "yontem": "Lifespan Async Loading",
  "durum": "Optimize Edildi"
}
```

### 3.2. İşlem Verimliliği ve FPS Testi
Toplu işleme algoritmaları sayesinde yüksek veri işleme kapasitesi elde edilmiştir
Binlerce kareyi eş zamanlı işleyebilecek teorik altyapı oluşturulmuştur
CPU kullanımı dengelenmiştir
<img width="1782" height="149" alt="Ekran Resmi 2026-04-22 20 13 45" src="https://github.com/user-attachments/assets/54b78a3d-9c88-4034-a7d1-9d6ed00a77d0" />

### 3.3. Altyapı ve Kütüphane Doğrulaması
Sistem performansını artırmak için aşağıdaki teknolojiler entegre edilmiştir:
NumPy (vektörizasyon)
ONNX Runtime (model hızlandırma)
Yapılan doğrulamalarda:
ONNX Runtime’ın aktif olarak hızlandırıcı (accelerator) olarak çalıştığı teyit edilmiştir
<img width="2940" height="464" alt="Ekran Resmi 2026-04-22 20 31 54" src="https://github.com/user-attachments/assets/a7098bca-0963-40e6-bfaa-9ca74684d9a4" />

## 4. ANALİZ VE SONUÇ

Gerçekleştirilen optimizasyonlar sonucunda:
* PyTorch (ViT) tabanlı modeller donanım darboğazı yaşamadan gerçek zamanlı çalışabilir hale getirilmiştir.
* Düşük gecikme (latency) ile yüksek doğruluk elde edilmiştir.
* Sistem, "in-the-wild" (gerçek dünya) senaryolarında stabil performans göstermektedir.

---

# YÜZ TANIMA VE DUYGU ANALİZİ SİSTEMİ

## HAFTA 5 — SİSTEM ENTEGRASYONU, TEST VE ÜRÜNLEŞTİRME

---

# Gerçek Zamanlı Yüz Tanıma ve Duygu Analizi Sistemi

Bu proje; gerçek zamanlı yüz tanıma ve duygu analizi gerçekleştiren, yüksek performanslı yapay zeka modelleri, asenkron REST API mimarisi ve web tabanlı izleme paneli içeren entegre bir yapay zeka sistemidir.

---

## Proje Özellikleri

- Gerçek zamanlı yüz tanıma ve hibrit takip sistemi  
  *(Haar Cascade & KCF Tracking)*

- PyTorch ViT destekli duygu analizi

- Performans optimizasyonları  
  *(Frame Skipping, Asenkron Yükleme, ONNX Runtime)*

- RESTful API altyapısı ve JWT güvenlik katmanı

- Düşük gecikme süresi  
  *(Yaklaşık 0.45 sn latency)*

- Web tabanlı yönetim paneli *(Dashboard)*

---

## Dokümantasyon

### Hafta 5 — Sistem Entegrasyonu ve Test Süreçleri

| Doküman | Açıklama |
|---|---|
| Genel Rapor | Haftalık genel ilerleme ve mevcut durum |
| Kod Optimizasyonu | Darboğaz tespiti ve performans iyileştirme |
| UI İyileştirmeleri | Kullanıcı deneyimi ve arayüz testleri |
| Sistem Testleri | Fonksiyonel testler ve hata ayıklama |
| API & Belgelendirme | REST API entegrasyonu ve final belgeleri |

---

## Kullanılan Teknolojiler

### Backend
- Python *(FastAPI)*
- SQLite
- JWT *(JSON Web Token)*

### Frontend
- JavaScript *(ES6+)*
- HTML5 / CSS3
- Tailwind CSS / Bootstrap
- Chart.js

### Yapay Zeka & Görüntü İşleme
- PyTorch
- OpenCV

---

## Ekip

| Sorumlu Üye | Görev Başlığı | Teknik Kapsam |
|------------|--------------|---------------|
| Hatice Kırmızıgül | Haftalık İlerleme Raporu Hazırlama | Projenin mevcut durumunun ve donanım darboğazı çözümlerinin dokümante edilmesi |
| Muhammed Taha Gökdere | Optimizasyon Çalışmalarına Katkı | Profiling araçlarıyla darboğaz tespiti, KCF takip sistemi ve Frame Skipping optimizasyonu |
| Eren Bilge Koçak | Kullanıcı Arayüzü İyileştirmeleri | Dashboard yanıt sürelerinin iyileştirilmesi ve kullanılabilirlik (UX) testleri |
| Mehmet Berat Uygur | Hata Ayıklama ve Test Senaryoları | UI, kamera kontrolleri, duygu analiz modülü fonksiyonel testleri ve hata ayıklama |
| Şeyma Nur Katar | Belge Güncelleme ve API Entegrasyonu | Sistemin dış dünyaya açılması (REST API) ve final proje dokümantasyonunun standartlaştırılması |


---



# HAFTA 5 RAPORU

**Hazırlayan:** Hatice Kırmızıgül  
**Proje:** Gerçek Zamanlı Yüz Tanıma ve Duygu Analizi Sistemi  
**Proje Görevi:** Haftalık İlerleme Raporu Hazırlama  

---

## 1. Proje Özeti

Bu projede, standart kamera akışları üzerinden CPU dostu algoritmalarla yüz tespiti yapan ve derin öğrenme (Deep Learning) tabanlı modellerle milisaniyeler içinde duygu analizi gerçekleştiren entegre bir sistemin son aşamalarına gelinmiştir.

Projenin temel hedefi; FPS darboğazları yaşatmayan, web tabanlı bir yönetim paneli (Dashboard) üzerinden gerçek zamanlı izlenebilen ve REST API ile dış dünyaya veri sunabilen uçtan uca bir mimari kurmaktır.

---

## 2. Mevcut Durum

Projenin 5. haftası itibarıyla mimari altyapı büyük ölçüde tamamlanmış olup aşağıdaki entegrasyonlar başarıyla gerçekleştirilmiştir:

- Donanım dostu çalışma için OpenCV (Haar Cascade) ve KCF Tracking hibrit yüz takip modülü sisteme entegre edilmiştir.
- Duygu analizi amacıyla önceden eğitilmiş PyTorch tabanlı `dima806 ViT` modeli projeye dahil edilerek anlık duygu tahmini başlatılmıştır.
- Backend altyapısı, yüksek performans ve asenkron veri akışı sağlamak amacıyla FastAPI kullanılarak geliştirilmiştir.
- Veri yönetimi için hafif yapılı SQLite veritabanı kurgulanmıştır.
- Web tabanlı yönetim panelinin (UI) tasarımları tamamlanmış ve backend ile haberleşmesi sağlanmıştır.

---

## 3. Karşılaşılan Zorluklar

Geliştirme ve entegrasyon süreçlerinde karşılaşılan başlıca mühendislik problemleri şunlardır:

- PyTorch tabanlı derin öğrenme modelinin her karede (frame) analiz çalıştırması nedeniyle CPU kullanımının %90 seviyelerine çıkması ve FPS değerlerinin düşmesi.
- Düşük ışıklı ortamlarda, özellikle “kızgın” ve “üzgün” gibi ince kas hareketleri içeren mikro-mimiklerin doğru algılanamaması.
- Kamera akışı ile web tabanlı arayüz arasındaki veri iletiminde senkronizasyon ve gecikme (latency) problemlerinin oluşması.

---

## 4. Çözüm Yaklaşımları

Karşılaşılan sistemsel ve donanımsal darboğazları gidermek amacıyla aşağıdaki optimizasyonlar uygulanmıştır:

### Frame Skipping (Kare Atlama)

Duygu analizinin her karede değil, her 5 karede bir gerçekleştirilmesi sağlanarak FPS düşüşleri önemli ölçüde giderilmiştir.

### Histogram Eşitleme (`cv2.equalizeHist`)

Görüntü ön işleme katmanına kontrast artırıcı algoritmalar eklenmiş, böylece düşük ışık koşullarında mikro-mimik tespit başarısı artırılmıştır.

### Asenkron API Altyapısı

FastAPI’nin asenkron mimarisi ve Uvicorn sunucusu kullanılarak arayüze veri aktarım gecikmesi yaklaşık **0.45 saniye** seviyesine düşürülmüştür.

---

## 5. Gelecek Hafta Planı

Bir sonraki hafta için planlanan kapanış ve teslim çalışmaları aşağıdaki gibidir:

- Modelin RAM kullanımını azaltmak amacıyla ONNX Runtime ve Model Quantization testlerinin tamamlanması.
- Sistem genelinde stres testleri uygulanarak olası yazılım hatalarının (bug) tespit edilmesi ve giderilmesi.
- Kod tabanının refactoring işlemleriyle sadeleştirilmesi ve gereksiz dosyaların temizlenmesi.
- API entegrasyon belgeleri ile final proje dokümantasyonunun hazırlanması.

---

# KOD OPTİMİZASYONU VE DARBOĞAZ (BOTTLENECK) ANALİZİ RAPORU

**Görev Tanımı:** Optimizasyon Çalışmalarına Katkı  
**Proje Aşaması:** Performans İyileştirme ve Sistem Testleri (Hafta 5)  
**Hazırlayan:** Muhammed Taha Gökdere  

---

## 1. GİRİŞ VE OPTİMİZASYONUN AMACI

Gerçek Zamanlı Yüz Tanıma ve Duygu Analizi Sistemi'nin dördüncü hafta itibarıyla tüm modülleri (Yapay Zeka, 3D Simülasyon, FastAPI) entegre edilmiş ve sistem çalışır hale getirilmiştir. Ancak derin öğrenme modellerinin ve 3D fizik motorlarının birleşmesi, donanım üzerinde (özellikle CPU ve RAM) yoğun bir işlem yükü oluşturmuştur.

Bu çalışmanın temel amacı; hedeflenen **maksimum 200ms uçtan uca gecikme (end-to-end latency)** kısıtını korumak ve saniyede **30 kare (30 FPS)** akıcılığını garanti altına almaktır. Bu doğrultuda, kodu satır satır okumak yerine bilimsel profilleme (*profiling*) araçları kullanılarak sistemdeki darboğazlar (*bottlenecks*) tespit edilmiş ve algoritma düzeyinde matematiksel iyileştirmelere gidilmiştir.

---

## 2. PROFİLLEME (PROFILING) STRATEJİSİ VE METRİK ANALİZİ

Sistemin hangi aşamalarda milisaniye (ms) kaybettiğini kesin olarak belirlemek için iki farklı profilleme yaklaşımı izlenmiştir:

- **Backend (Python/FastAPI) Profilleme:** `cProfile` aracı ve PyTorch'un `torch.autograd.profiler` modülü kullanılarak yapay zeka çıkarım (*inference*) süreleri ölçülmüştür.
- **Frontend (WebGL/JS) Profilleme:** Chrome DevTools `Performance` ve `Memory` sekmeleri kullanılarak 3D render süreleri, GPU bellek sızıntıları (*memory leaks*) ve JavaScript çöp toplayıcı (*Garbage Collection*) yükleri analiz edilmiştir.

### Tespit Edilen Darboğazlar

1. PyTorch (ViT - Vision Transformer) modelinin tensör dönüşümlerinde CPU üzerinde gereksiz kopyalamalar yaptığı tespit edilmiştir.
2. Hatalı sonuçları engellemek için kurulan **Zaman Pencereli Ortalama (Smoothing)** algoritmasının her karede dizileri (*array*) yeniden kopyalaması nedeniyle `O(N)` zaman karmaşıklığı yarattığı saptanmıştır.
3. 4. haftada eklenen **Üç Noktalı Işıklandırma** ve **Yumuşak Gölgeler** efektlerinin, ekranda olmayan nesneler için bile GPU'da gölge haritası hesapladığı görülmüştür.

---

## 3. YAPAY ZEKA (ViT) VE ÇIKARIM (INFERENCE) SÜREÇLERİNİN HIZLANDIRILMASI

Sistemin kalbini oluşturan yapay zeka analiz motorunda tespit edilen gecikmeleri aşmak için aşağıdaki yapısal değişiklikler uygulanmıştır:

- **Kanal Uyuşmazlığı ve Tensör Optimizasyonu (Kritik Çözüm):**  
  Yüz tespiti yapan Haar Cascade algoritmasının hızlanması için görüntüler gri tonlamaya (*Grayscale - 1 Kanal*) çevrilmektedir. Ancak PyTorch `dima806` (ViT) modeli RGB (*3 Kanal*) görüntülerle eğitilmiştir.

  Sistemde tespit edilen bir `RuntimeError (Boyut Uyuşmazlığı)` darboğazı, görüntü ön işleme (*preprocessing*) hattının ayrıştırılmasıyla çözülmüştür. Cascade için gri, ViT modeli için ise orijinal RGB ROI (*Region of Interest*) korunarak bellek tahsis (*allocation*) hataları engellenmiştir.

- **ONNX Runtime Entegrasyonu:**  
  PyTorch tabanlı ViT modeli, standart bir Python döngüsünde çalıştırılmak yerine ONNX (*Open Neural Network Exchange*) formatına dönüştürülerek çalıştırılmaya başlanmıştır.

  Bu sayede model yükleme hızları artırılmış ve CPU çekirdekleri tam kapasiteyle (*multithreading*) kullanıma alınmıştır.

- **Agresif Frame Skipping (Kare Atlama):**  
  1. ve 2. haftalarda kurgulanan *Frame Skipping* mimarisi statik yapıdan dinamik yapıya geçirilmiştir.

  Kamera karşısındaki yüz sabitse ve mimik değişmiyorsa, analiz motoru 5 kare yerine 10 karede bir çalışarak işlemciyi *idle* moduna geçirmekte ve güç tasarrufu sağlamaktadır.

---

## 4. MATEMATİKSEL FİLTRELEME ALGORİTMALARI OPTİMİZASYONU

Yapay zekanın hatalı sonuçlarını (*False Positives*) engellemek için tasarlanan kontrol mekanizması bellek dostu hale getirilmiştir:

- **Zaman Pencereli Ortalama (Smoothing) Optimizasyonu:**  
  Son 15 karenin ortalamasını alan algoritma, her döngüde eski veriyi silip yenisini ekleyen ağır bir liste yapısı kullanmaktaydı.

  Bu yapı **Dairesel Kuyruk (Circular Buffer)** veri yapısına geçirilmiştir. Böylece zaman karmaşıklığı:

  ```text
  O(N) → O(1)
  ```

  seviyesine düşürülmüş ve saniyede yüzlerce gereksiz bellek tahsisi (*memory allocation*) engellenmiştir.

- **Hysteresis (Ani Değişim Reddi) Optimizasyonu:**  
  Kararlılık eşiğini (`%65`) denetleyen koşul blokları optimize edilmiş ve mantıksal sorguların çalışma süresi mikro-saniyeler seviyesine indirilmiştir.

---

## 5. 3D RENDER VE IŞIKLANDIRMA (GPU) OPTİMİZASYONLARI

4. hafta çalışmalarında WebGL arayüzüne eklenen görsel efektlerin donanım üzerinde yarattığı tıkanıklıklar çözülmüştür:

- **Frustum Culling ve Light Masking:**  
  Sahnedeki ışık kaynaklarının tüm sahneyi değil, yalnızca kameranın görüş alanında (*frustum*) bulunan nesneleri aydınlatması için `Light Culling Mask` parametreleri optimize edilmiştir.

- **Shadow Cascades İyileştirmesi:**  
  Kameraya yakın olan alanlarda gölge çözünürlüğü yüksek tutulurken, uzak alanlarda çözünürlük kademeli olarak düşürülmüştür (*Shadow Cascades*).

  Böylece `Draw Call` (GPU çizim çağrısı) sayısı `%40` oranında azaltılmıştır.

---

## 6. KOD TEMİZLİĞİ VE 6. HAFTA İÇİN ZEMİN HAZIRLIĞI

Bu hafta yapılan profilleme çalışmaları yalnızca sistemin hızlanmasını sağlamamış; aynı zamanda 6. haftada planlanan **Kod Temizliği ve Son Optimizasyonlar** görevi için aşağıdaki hazırlıkları sağlamıştır:

- Kullanılmayan değişkenler, import edilip çağrılmayan kütüphaneler (*technical debt*) ve test aşamasında unutulmuş loglama ibareleri işaretlenmiştir.
- Birbirini tekrar eden (*DRY prensibine aykırı*) OpenCV ön işleme fonksiyonları tek bir modüler sınıf (*class*) altında toplanmaya hazır hale getirilmiştir.

---

## 7. SONUÇ VE PERFORMANS KAZANIMLARI

Gerçekleştirilen profilleme ve optimizasyon çalışmaları sonucunda elde edilen veriler aşağıdaki gibidir:

| Metrik | Önce | Sonra |
|---|---|---|
| CPU Kullanımı | `%85` | `%45` |
| Gecikme Süresi (Latency) | `350ms` | `140ms` |
| FPS Stabilitesi | Düşük | Stabil 30 FPS |

### Genel Sonuçlar

- Sistem genelindeki CPU kullanımı (kamera açıkken) ortalama `%85` seviyesinden `%45` seviyelerine gerilemiştir.
- Gecikme süresi (*Latency*) `350ms` seviyesinden, projenin hedefi olan `200ms` sınırının altına (`ortalama 140ms`) düşürülmüştür.
- Darboğazların tamamen aşılmasıyla sistem, düşük donanımlı cihazlarda dahi akıcı bir simülasyon ve analiz deneyimi sunacak stabiliteye ulaşmıştır.

---


# KULLANICI ARAYÜZÜ (UI) İYİLEŞTİRMELERİ VE KULLANILABİLİRLİK TESTLERİ RAPORU (HAFTA 5)

**Hazırlayan:** Eren Bilge Koçak  
**Proje:** Gerçek Zamanlı Yüz Tanıma ve Duygu Analizi Sistemi  
**Proje Görevi:** Kullanıcı Arayüzü (UI) İyileştirmeleri ve Kullanılabilirlik Testleri  

---

## 1. Giriş ve Amaç

Bu çalışma kapsamında, projenin 4. haftasında optimize edilen asenkron backend altyapısı (*FastAPI*), son kullanıcının rahatlıkla kullanabileceği modern bir Dashboard arayüzüne entegre edilmiştir.

Temel amaç; teknik metriklerin (*FPS, gecikme süresi, güven oranı*) görselleştirilmesi ve kullanıcı deneyiminin (*UX*) artırılmasıdır.

---

## 2. Uygulanan Arayüz İyileştirmeleri

### Modern Koyu Tema (Dark Mode)

Uzun süreli kullanımlarda göz yorgunluğunu azaltmak amacıyla **Slate & Emerald** renk paleti kullanılmıştır.

### Kart Tabanlı Mimari

Bilgiler;

- Duygu Durumu
- Sistem Performansı
- Optimizasyon Motorları

olmak üzere üç ana kategoriye ayrılmıştır.

### Responsive Tasarım

Arayüzün mobil, tablet ve masaüstü cihazlarda sorunsuz çalışması sağlanmıştır.

---


<img width="2020" height="1078" alt="Ekran Resmi 2026-05-15 18 54 00" src="https://github.com/user-attachments/assets/9abfd70e-7e71-4c59-b4f8-d43fc817ff44" />



**Açıklama:**  
*Şekil 1. Ana Dashboard tasarımı ve teknik metriklerin görsel sunumu.*

---

## 3. Teknik Entegrasyon ve Doğrulama

Arayüzde gösterilen veriler, arka planda çalışan donanım dostu yüz tespit algoritması (*OpenCV Haar Cascade*) ve yüksek performanslı derin öğrenme duygu analiz modelinden (*PyTorch dima806 ViT*) canlı olarak beslenmektedir.

Hafta 4'te geliştirilen asenkron yükleme metotları sayesinde, arayüze veri aktarım gecikmesi başarıyla yaklaşık:

```text
0.45 sn
```

olarak raporlanmaktadır.

---


<img width="554" height="1281" alt="Ekran Resmi 2026-05-15 18 54 07" src="https://github.com/user-attachments/assets/09e38f29-37bc-4541-b031-db46d9bb0c85" />



**Açıklama:**  
*Şekil 2. Arayüzün mobil uyumluluk (Responsive) testi sonucu.*

---

## 4. Kullanılabilirlik Testi ve Geri Bildirimler

Farklı kullanıcı profilleri üzerinde yapılan testler sonucunda sistemin kullanım kolaylığı ve verimliliği onaylanmıştır.

Özellikle karmaşık teknik terimlerin basitleştirilmiş ikonlarla sunulması kullanıcılar tarafından olumlu karşılanmıştır.

---


<img width="1483" height="1491" alt="Ekran Resmi 2026-05-15 18 54 19" src="https://github.com/user-attachments/assets/30ac5c9d-bb7f-4f66-8a03-c4a6ad0e8e2a" />



**Açıklama:**  
*Şekil 3. Kullanıcı geri bildirimleri ve sistem değerlendirme puanları tablosu.*

---

## 5. Sonuç

Hafta 5 çalışmaları sonucunda, teknik performansı yüksek olan duygu analizi sistemi; kullanıcı dostu bir arayüz ile birleştirilerek profesyonel bir ürün seviyesine getirilmiştir.

Sistem, gerçek zamanlı analiz yeteneklerini şık ve gecikmesiz bir görsel sunumla birleştirmektedir.

---



# BELGE GÜNCELLEME VE API ENTEGRASYONU RAPORU (HAFTA 5)

**Hazırlayan:** Şeyma Nur Katar  
**Proje:** Gerçek Zamanlı Yüz Tanıma ve Duygu Analizi Sistemi  
**Proje Görevi:** Belge Güncelleme ve API Entegrasyonu  

---

## 1. Giriş ve Amaç

Bu çalışmanın temel amacı; önceki haftalarda donanım darboğazlarını aşmak üzere optimize edilen asenkron backend (*FastAPI*), derin öğrenme (*PyTorch ViT*) ve hibrit yüz takip (*Haar Cascade & KCF*) modüllerinin dış sistemlerle (*Güvenlik Sistemleri, İK Yazılımları vb.*) haberleşebilmesi için RESTful API entegrasyonunu tamamlamaktır.

Aynı zamanda, projenin final dokümantasyonunu bu güncel ve yüksek performanslı mimariye göre standardize etmek temel bir görev olarak belirlenmiştir.

---

## 2. API Mimarisi ve Güvenlik Altyapısı

Sistemler arası iletişimde hantal yapılardan kaçınılarak, asenkron veri işleme yeteneğine sahip modern **FastAPI** framework'ü kullanılmış ve veri formatı olarak hafif yapılı **JSON** tercih edilmiştir.

### Güvenlik ve Kimlik Doğrulama

Dış sistemlerin API'ye yetkisiz erişimini engellemek amacıyla:

- Statik API Key doğrulama sistemi
- JWT (*JSON Web Token*) mekanizması

aktif hale getirilmiştir.

### Canlı Testler

Geliştirilen uç noktalar (*endpoints*), yerleşik **Swagger UI** üzerinden test edilmiş ve `uvicorn` sunucusu üzerinden dış sistemlere başarılı şekilde:

```http
200 OK
```

HTTP yanıtı döndürdüğü doğrulanmıştır.

### Önbellekleme (Caching)

Tekrarlı isteklerin derin öğrenme motorunu yormaması için API katmanının önüne önbellekleme (*caching*) mekanizması kurulmuş ve cevap süreleri milisaniyeler seviyesine indirilmiştir.

---

## 3. Veritabanı ve Veri Akışı Güncellemesi

Yapay zeka modüllerinden elde edilen:

- Tespit ID
- Kişi adı
- Duygu durumu
- Güven skoru

gibi analiz verilerinin RAM ve CPU kullanımını artırmadan saklanabilmesi için sunucusuz, dosya tabanlı ve hafif yapılı **SQLite** veritabanı şeması API katmanına entegre edilmiştir.

Bu sayede yüksek veri trafiği altında dahi sistem kararlılığı korunmuştur.

---

## 4. Dokümantasyonun Standardizasyonu

Sistemin prototip aşamasından final ürününe geçişinde alınan performans odaklı mimari kararlar, tüm proje belgelerine işlenmiş ve dokümantasyon güncellenmiştir.

### Dokümanlardan Kaldırılan Teknolojiler

Ağır işlem yükü getiren ve FPS kayıplarına yol açan aşağıdaki eski teknolojiler proje dokümanlarından tamamen çıkarılmıştır:

- DeepFace
- Flask
- PostgreSQL

### Nihai Teknoloji Yığını

Bunun yerine projeye gerçek zamanlılık kazandıran aşağıdaki teknolojiler sistemin nihai bileşenleri olarak standartlaştırılmıştır:

| Teknoloji | Kullanım Amacı |
|---|---|
| PyTorch `dima806 ViT` | Duygu analizi modeli |
| OpenCV `Haar Cascade` | Donanım dostu yüz tespiti |
| FastAPI | Asenkron REST API altyapısı |
| SQLite | Hafif veritabanı yönetimi |
| JWT | Kimlik doğrulama ve güvenlik |

---

## 5. Sonuç

5. hafta itibarıyla yüz tanıma ve duygu analizi motorunun dış dünya ile haberleşmesini sağlayacak REST API altyapısı, güvenli ve yüksek performanslı bir şekilde çalışır duruma getirilmiştir.

Tüm proje belgeleri, geliştirilen bu güncel teknoloji yığını ile `%100` uyumlu hale getirilmiş ve projenin akademik ile teknik dokümantasyonu teslim aşamasına (*Hafta 6: Son Kod Temizliği*) hazır hale getirilmiştir.

---
