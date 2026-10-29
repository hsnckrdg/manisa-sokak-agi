# Manisa Kent Merkezi Sokak Ağı Analizi

Bu proje, Manisa'nın Şehzadeler ve Yunusemre ilçelerindeki yol ağını karmaşık ağ ve sosyal ağ analizi yöntemleriyle incelemektedir.

OpenStreetMap verileri kullanılarak kavşaklar düğüm, yol parçaları ise kenar olarak modellenmiştir.

## Araştırma Soruları

1. Ağ merkeziyeti yüksek kavşakların çevresinde ticari POI yoğunluğu daha fazla mıdır?
2. Kritik yol parçalarının tek tek kapanması kent içi erişilebilirliği ne ölçüde etkilemektedir?

## Veri Kaynağı

- OpenStreetMap
- OSMnx
- Overpass API

İncelenen bölgeler:

- Şehzadeler / Manisa
- Yunusemre / Manisa

## Ağ Özellikleri

- Düğüm sayısı: 11.152
- Kenar sayısı: 16.429
- Toplam yol uzunluğu: yaklaşık 2.209,82 km
- Ortalama derece: 2,946
- Ağ yoğunluğu: 0,000264
- Bağlı bileşen sayısı: 1
- Ortalama clustering katsayısı: 0,04646
- Degree assortativity: 0,10947
- Ortalama en kısa yol: yaklaşık 17,68 km
- Yaklaşık ağ çapı: 65,83 km

## Kullanılan Analizler

- Degree Centrality
- Betweenness Centrality
- Closeness Centrality
- PageRank
- Louvain topluluk tespiti
- Leiden topluluk tespiti
- ARI ve NMI kararlılık analizi
- Configuration Model null model analizi
- Power Law, Lognormal ve Exponential dağılım karşılaştırması
- POI yoğunluğu analizi
- Spearman korelasyon analizi
- Kritik yol kapanma senaryoları

## Derece Dağılımı

Ağdaki düğümlerin derece değerleri 1 ile 6 arasında değişmektedir.

Power law analizi sonucunda:

- Alpha: 2,466
- xmin: 2
- KS değeri: 0,492

olarak bulunmuştur.

Model karşılaştırmalarında lognormal dağılımın power law ve exponential modellere göre daha iyi uyum gösterdiği görülmüştür.

Bu nedenle Manisa sokak ağının derece dağılımı klasik scale-free ağ yapısını güçlü biçimde desteklememektedir.

## Merkeziyet Analizi

Ağ üzerinde dört merkeziyet ölçüsü hesaplanmıştır:

- Degree Centrality
- Betweenness Centrality
- Closeness Centrality
- PageRank

Ağın büyüklüğü nedeniyle betweenness centrality yaklaşık olarak 300 örnek düğüm kullanılarak hesaplanmıştır.

Betweenness açısından en önemli kavşaklardan bazıları:

- 2251603222
- 983383019
- 2251420435
- 2251463963
- 2351998468

Merkeziyet ölçüleri arasındaki en güçlü ilişkilerden biri Degree Centrality ile PageRank arasında görülmüştür.

Spearman korelasyonu:

- Degree - PageRank: 0,734
- Degree - Betweenness: 0,452

## Topluluk Analizi

Topluluk tespiti için Louvain ve Leiden algoritmaları kullanılmıştır.

Her iki algoritma 10 farklı rastgele başlangıç değeri ile çalıştırılmıştır.

Louvain sonuçları:

- Topluluk sayısı: 64-69
- Modularity: yaklaşık 0,9588-0,9602
- Ortalama ARI: 0,7023
- Ortalama NMI: 0,8856

Leiden sonuçları:

- Topluluk sayısı: 65-71
- Modularity: yaklaşık 0,9609-0,9619
- Ortalama ARI: 0,7068
- Ortalama NMI: 0,8918

Leiden algoritması hem modularity hem de kararlılık açısından Louvain algoritmasına göre az farkla daha iyi sonuç vermiştir.

## Null Model Analizi

Gerçek ağın yapısını rastgele ağlarla karşılaştırmak amacıyla 100 adet Configuration Model ağı oluşturulmuştur.

### Clustering

Gerçek ağ:

0,046464

Null model ortalaması:

0,000133

Z-skoru:

447,857

### Ortalama Yol Uzunluğu

Gerçek ağ:

44,1681 adım

Null model ortalaması:

10,8489 adım

Z-skoru:

302,570

### Modularity

Gerçek ağ:

0,9602

Null model ortalaması:

0,6887

Z-skoru:

316,673

Sonuçlar gerçek yol ağının rastgele oluşturulan ağlardan yapısal olarak belirgin biçimde farklı olduğunu göstermektedir.

## POI Analizi

OpenStreetMap üzerinden ticari ve kamusal ilgi noktaları toplanmıştır.

Toplam:

- 429 benzersiz POI
- 198 Shop
- 231 Amenity

Her kavşağın 500 metre çevresindeki POI sayısı hesaplanmıştır.

Tüm ağ için:

- Ortalama POI sayısı: 7,18
- Maksimum POI sayısı: 121
- En az bir POI bulunan kavşak: 4.802

Betweenness Centrality ile 500 metre çevresindeki POI yoğunluğu arasındaki Spearman korelasyonu:

- Rho: 0,2096
- p-değeri: yaklaşık 5,39 × 10^-111

Bu sonuç zayıf fakat istatistiksel olarak anlamlı pozitif bir ilişki göstermektedir.

## Kritik Yol Analizi

Yaklaşık edge betweenness centrality kullanılarak ilk 10 kritik yol segmenti belirlenmiştir.

Bu yollar ağdan tek tek kaldırılarak 150 sabit örnek düğüm üzerinde ortalama en kısa yol değişimi hesaplanmıştır.

En yüksek erişim bozulması:

2251463963 - 2251603222

kenarında görülmüştür.

Bu yol segmenti kaldırıldığında ortalama yol mesafesi yaklaşık:

%0,1086

artmıştır.

İlk 10 kritik segmentin 6 tanesi OpenStreetMap verisinde Mehmetçik Caddesi olarak kayıtlıdır.

Diğer 4 kritik segmentin OSM `name` alanı boş olduğu için bu segmentlere doğrulanmamış yol isimleri verilmemiştir.

Tekil yol kapanma senaryolarının hiçbirinde örnek düğüm çiftleri arasında tamamen kopuk bağlantı oluşmamıştır.

Bu sonuç, ağın bazı kritik koridorlara sahip olmasına rağmen alternatif güzergâhlar sayesinde belirli ölçüde dayanıklı olduğunu göstermektedir.

## Etkileşimli Ağ

Proje kapsamında tarayıcıda çalışan etkileşimli bir ağ görselleştirmesi hazırlanmıştır.

Tarayıcı performansını korumak amacıyla etkileşimli görünümde:

- 1.200 düğüm
- 1.306 kenar

kullanılmıştır.

Etkileşimli ağ özellikleri:

- Düğüm ID araması
- Leiden topluluk filtresi
- Pan ve zoom
- Düğüme tıklayarak detay görüntüleme
- Degree Centrality görüntüleme
- Betweenness Centrality görüntüleme
- Closeness Centrality görüntüleme
- PageRank görüntüleme
- 500 metre çevresindeki POI sayısını görüntüleme
- Kritik yolları kırmızı renkle gösterme

Etkileşimli ağ kişisel portfolyo sitesine de gömülmüştür.

## Yeniden Üretilebilirlik

Projede rastgele örnekleme kullanılan analizlerde sabit rastgelelik değeri kullanılmıştır.

SEED = 42

Büyük ağ nedeniyle bazı hesaplamalar yaklaşık yöntemlerle yapılmıştır:

- Betweenness Centrality: 300 örnek düğüm
- Edge Betweenness: 300 örnek düğüm
- Ortalama en kısa yol ve çap: 250 örnek düğüm
- Kritik yol senaryoları: 150 örnek düğüm
- Null model sayısı: 100

## Kurulum

Gerekli Python paketleri aşağıdaki komut ile kurulabilir:

```bash
pip install -r requirements.txt
```

Jupyter Notebook başlatmak için:

```bash
jupyter notebook
```

## Kullanılan Teknolojiler

- Python
- Jupyter Notebook
- NetworkX
- OSMnx
- GeoPandas
- Pandas
- NumPy
- SciPy
- Matplotlib
- scikit-learn
- igraph
- leidenalg
- powerlaw
- Requests

## Proje Sınırlılıkları

OpenStreetMap kullanıcı katkılı bir veri kaynağı olduğu için bütün yol ve POI kayıtlarının eksiksiz olduğu garanti edilemez.

Şehzadeler bölgesindeki shop verisi toplanırken Overpass API kaynaklı olarak 16 alt bölgeden birinde veri alınamamıştır.

Bazı merkeziyet ve mesafe hesaplamaları ağın büyüklüğü nedeniyle örneklemeli yöntemlerle gerçekleştirilmiştir.

Configuration Model coğrafi konum, gerçek yol geometrisi ve yol yapım kısıtlarını dikkate almamaktadır.

Etkileşimli ağda performans nedeniyle tüm 11.152 düğüm yerine 1.200 önemli düğüm gösterilmektedir.

## Yapay Zekâ Kullanımı

Projede yapay zekâ araçlarından kod geliştirme, hata ayıklama, analiz sonuçlarının yorumlanması ve dokümantasyon hazırlanması aşamalarında yardımcı araç olarak yararlanılmıştır.

Raporda kullanılan sayısal sonuçlar Python ortamında çalıştırılan analizlerden elde edilmiştir.

## Veri Lisansı

OpenStreetMap verileri Open Database License (ODbL) kapsamında kullanılmaktadır.

© OpenStreetMap contributors