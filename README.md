# Hastane Veri Seti - Gerçekçi Simülasyon

Bu depo, uçtan uca bir veri bilimi projesinin ilk aşaması olan veri toplama ve temizleme adımlarında pratik yapmak amacıyla özel olarak oluşturulmuş sentetik bir hastane veri setini barındırmaktadır.

## Proje Amacı

Gerçek dünya veri setleri genellikle eksik değerler, hatalı girişler, tutarsız formatlar ve aykırı değerler gibi "kirli" verilerle doludur. Bu proje, bu tür gerçek hayat senaryolarını simüle etmek ve bu kirlilikleri ele alma becerilerini geliştirmek için bir temel sağlamaktadır.

Bu veri seti, gelecekteki bir veri bilimi projem için başlangıç noktası olacak ve veri toplama (veri tabanından simüle edilmiş), veri temizleme, veri dönüştürme, modelleme ve görselleştirme (Tableau gibi araçlarla raporlama) süreçlerini baştan sona uygulamamı sağlayacaktır.

## Veri Seti Açıklaması

Veri seti, hayali bir hastanenin hasta kayıtlarını temsil etmektedir ve aşağıdaki sütunları içermektedir:

* `Patient_ID`: Benzersiz hasta ID numarası (Sayısal)
* `Age`: Hastanın yaşı
* `Gender`: Hastanın cinsiyeti
* `Condition`: Hastalık kondisyonu (Örn: Influenza, Diabetes)
* `Procedure`: Uygulanan prosedürler (Örn: Surgery, Blood Test)
* `Cost`: İşlemlerin maliyeti
* `Length_of_stay`: Yatış süresi (Gün)
* `Readmission`: Yeniden kabul edilme durumu (Evet/Hayır)
* `Outcome`: Sonuç (Örn: Discharged, Deceased, Stable)
* `Satisfaction`: Memnuniyet oranı (1-4 arası sayısal)

## Veri Seti Nasıl Oluşturuldu?

Bu veri seti, Python programlama dili ve `pandas`, `numpy`, `random` kütüphaneleri kullanılarak sentetik olarak üretilmiştir. Amacımız, başlangıçta temiz bir veri yapısı oluşturmak ve ardından buna bilerek ve sistematik olarak çeşitli "kirlilikler" eklemektir.

### Kirlilik Ekleme Stratejisi (Orta Düzey)

Veri setine orta düzeyde gerçekçilik katmak için aşağıdaki türlerde kirlilikler eklenmiştir:

1.  **Eksik Değerler (Missing Values):**
    * `Condition`, `Procedure`, `Cost`, `Outcome`, `Satisfaction`, `Length_of_stay` sütunlarına rastgele %5-10 oranında eksik değer (`NaN`) eklenmiştir.
2.  **Çift Kayıtlar (Duplicate Records):**
    * Veri setinin %2-3'ü oranında tamamen veya kısmen çift kayıtlar eklenmiştir. Bazı çift kayıtların `Patient_ID`'leri farklılaştırılarak kısmi mükerrerlik simüle edilmiştir.
3.  **Veri Tipi Hataları (Data Type Inconsistencies):**
    * `Age`, `Cost`, `Length_of_stay` gibi sayısal olması gereken sütunlara metin (`"yirmi"`, `"$1500"`, `"iki hafta"`) veya anlamsız karakterler girilmiştir.
    * `Satisfaction` (1-4 arası sayısal olması beklenirken) sütununa metin (`"High"`, `"Not Rated"`) veya beklenen aralık dışı sayılar (`5`, `0`) eklenmiştir.
4.  **Yazım Yanlışları ve Tutarsızlıklar (Typos and Inconsistencies):**
    * `Gender` sütununda büyük/küçük harf tutarsızlıkları (`"Male"`, `"MALE"`, `"m"`) veya farklı ifadeler (`"Erkek"`, `"Unspecified"`) kullanılmıştır.
    * `Condition`, `Procedure`, `Outcome` gibi metinsel sütunlarda rastgele yazım hataları, fazla boşluklar veya büyük/küçük harf değişiklikleri yapılmıştır.
5.  **Aykırı Değerler (Outliers):**
    * `Age` (0-1, 100+), `Cost` (çok düşük/yüksek) ve `Length_of_stay` (0, çok uzun) gibi sayısal sütunlara gerçekçi olmayan aykırı değerler eklenmiştir.
    * `Satisfaction` sütununa da (0, 5, 6, 10 gibi) aykırı sayısal değerler dahil edilmiştir.

Bu yapı, bir veri bilimci veya veri analisti için gerçek dünya veri problemlerine yaklaşırken karşılaşabileceği zorlukları yaşayabileceği zengin bir ortam sunmaktadır.

## Gelecek Planlarım

Bu veri seti, ileride yapacağım uçtan uca veri bilimi projem için temel teşkil edecektir. Bu proje kapsamında aşağıdaki adımları tamamlamayı hedefliyorum:

* **Veri Toplama:** Oluşturulan bu veri setini bir veritabanına (örneğin PostgreSQL, SQLite) yükleyerek gerçek bir veri toplama sürecini simüle etmek.
* **Veri Temizleme ve Dönüştürme (ETL):** Python (Pandas), SQL veya diğer ETL araçlarını kullanarak veri setindeki tüm kirlilikleri temizlemek ve analiz için uygun hale getirmek.
* **Veri Analizi ve Modelleme:** Temizlenmiş veri üzerinde keşifsel veri analizi (EDA) yapmak, potansiyel içgörüler elde etmek ve uygun istatistiksel veya makine öğrenimi modelleri geliştirmek.
* **Veri Görselleştirme ve Raporlama:** Temizlenmiş ve analiz edilmiş veriyi Tableau veya Power BI gibi araçlar kullanarak etkileşimli panolar ve raporlar halinde sunmak.


---
