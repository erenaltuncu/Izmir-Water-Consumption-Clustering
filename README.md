#  İzmir İli Su Tüketim Davranışlarının Makine Öğrenmesi ile Analizi

**Öğrenci:** Eren Altuncu  
**Danışman:** Prof. Dr. Muhammed Maruf Öztürk

##  Proje Özeti
Bu proje, İzmir genelindeki mahallelerin su tüketim verilerini analiz ederek tüketim alışkanlıklarını modeller. K-Means kümeleme algoritması kullanılarak "Yazlıkçı", "Standart" ve "Aşırı Tüketim (Anomali)" bölgeleri tespit edilmiştir. Amaç, şebeke kayıp/kaçaklarını ve altyapı risklerini veri odaklı yönetmektir.

##  Kullanılan Teknolojiler
* **Python 3.x**
* **Pandas:** Büyük veri işleme ve temizleme (BOM encoding fix, optimizasyon).
* **Scikit-Learn:** K-Means Clustering ve StandardScaler.
* **Seaborn/Matplotlib:** Veri görselleştirme.

##  Metodoloji

### 1. Optimal Küme Sayısı (Elbow Metodu)
Veri setindeki tüketim davranışlarını en iyi ayrıştıran küme sayısının 4 olduğu matematiksel olarak doğrulanmıştır.

![Elbow Grafiği](elbow_method.png)

### 2. Segmentasyon Sonuçları
Mahalleler tüketim karakteristiğine göre 4 ana gruba ayrılmıştır. Kırmızı/Yeşil noktalar (Anomaliler) ve Mavi noktalar (Yazlıkçılar) açıkça görülmektedir.

![Scatter Plot Analizi](scatter_plot.png)

##  Kritik Bulgular (Anomali Tespiti)
Model, aşağıdaki bölgelerde **acil müdahale gerektiren** aşırı tüketim (kaçak şüphesi) tespit etmiştir:

| İlçe | Mahalle | Ortalama Tüketim (m³) | Durum | Eylem Planı |
|---|---|---|---|---|
| GAZİEMİR | GAZİKENT | **185.57** |  ANOMALİ | Kaçak ekibi yönlendirilmeli |
| KARŞIYAKA | M. KEMAL | **118.48** |  ANOMALİ | Altyapı kontrol edilmeli |
| ALİAĞA | BOZKÖY | 19.87 |  YAZLIKÇI | Yazın basınç artırılmalı |

##  Gelecek Tüketim Tahmini (Forecasting)

Projenin ikinci aşamasında, İzmir'in gelecekteki su tüketimini tahmin etmek için **AdaBoost** ve **Random Forest** regresyon algoritmaları kullanılmıştır.

* **Veri Temizliği:** 2020 yılındaki veri hataları (Outliers) istatistiksel yöntemlerle temizlenerek model başarısı artırılmıştır.
* **Başarı Skoru:** Modelimiz **R² = 0.886** skoruna ulaşarak, akademik literatürdeki benzer çalışmalarla (Örn: R²=0.896) yarışır düzeye gelmiştir.

![Tahmin Grafiği](prediction_graph.png)

**En Etkili Faktörler:**
Modelin tahmin yaparken en çok "Son 3 ayın ortalamasına" (Moving Average) dikkat ettiği görülmüştür.

![Öznitelik Önemi](feature_importance.png)

##  Kurulum ve Çalıştırma

1. Repoyu klonlayın:
   ```bash
   git clone https://github.com/erenaltuncu/Izmir-Water-Consumption-Clustering.git

2. Gerekli paketleri yükleyin: 
pip install -r requirements.txt

3. Notebook'u çalıştırın:
jupyter notebook main.ipynb
