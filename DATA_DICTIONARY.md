# Veri Sözlüğü

## manisa_nodes.csv

| Alan | Açıklama |
|---|---|
| node_id | OpenStreetMap kavşak düğüm kimliği |
| lon | Düğümün boylam değeri |
| lat | Düğümün enlem değeri |
| degree | Düğümün ağdaki bağlantı sayısı |

## manisa_edges.csv

| Alan | Açıklama |
|---|---|
| source | Yol segmentinin başlangıç düğümü |
| target | Yol segmentinin bitiş düğümü |
| length_m | Yol segmentinin metre cinsinden uzunluğu |
| highway | OpenStreetMap yol sınıfı |
| name | OpenStreetMap yol adı; bazı segmentlerde boş olabilir |

## centrality_results.csv

| Alan | Açıklama |
|---|---|
| node_id | Kavşak düğüm kimliği |
| degree | Degree centrality |
| betweenness | Yaklaşık ağırlıklı betweenness centrality |
| closeness | Yol uzunluğu ağırlıklı closeness centrality |
| pagerank | PageRank merkeziyet değeri |

## manisa_poi.csv

| Alan | Açıklama |
|---|---|
| lon | POI boylamı |
| lat | POI enlemi |
| category | POI ana kategorisi |
| amenity / shop | OpenStreetMap POI sınıfı |

POI verileri kafe, restoran, fast-food, banka, eczane, pazar yeri ve shop etiketli ticari noktaları içermektedir.

## poi_betweenness_analysis.csv

| Alan | Açıklama |
|---|---|
| node_id | Kavşak kimliği |
| betweenness | Kavşağın betweenness centrality değeri |
| poi_500m | Kavşağın 500 metre çevresindeki POI sayısı |

## kritik_yol_sonuclari_final.csv

| Alan | Açıklama |
|---|---|
| source | Kritik yol başlangıç düğümü |
| target | Kritik yol bitiş düğümü |
| edge_betweenness | Yolun edge betweenness değeri |
| road_name | OSM yol adı; bulunmuyorsa adsız segment |
| change_percent | Yol kaldırıldığında ortalama yol mesafesindeki yüzde değişim |
| disconnected | Örneklem içinde bağlantısı kopan çift sayısı |

## manisa.graphml

Ağın GraphML biçimindeki kaydıdır.

## interactive_network_FINAL2.html

Analizin 1.200 önemli düğüm ve 1.306 kenardan oluşan etkileşimli web görselleştirmesidir.