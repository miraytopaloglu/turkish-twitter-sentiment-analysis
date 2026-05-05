# Türkçe Twitter Duygu Analizi (Turkish Twitter Sentiment Analysis)

Bu depo, Türkçe Twitter verileri kullanılarak gerçekleştirilen 3 sınıflı (Pozitif, Negatif, Nötr) duygu analizi tez çalışmasının kaynak kodlarını ve analiz sonuçlarını içermektedir.

## Proje Özeti
Çalışmanın temel amacı, Türkçe gibi sondan eklemeli ve karmaşık bir dilde, klasik makine öğrenmesi algoritmalarının (SVM, Lojistik Regresyon, Random Forest vb.) ve melez (Ensemble) yapıların performansını ölçmek ve optimize etmektir. 

## Veri Seti ve Metodoloji
* **Veri Dengeleme:** Başlangıç veri setindeki aşırı "Nötr" sınıfı yığılmasını gidermek amacıyla literatürden 11.111 satırlık ikincil bir veri seti projeye entegre edilmiştir. Toplam **24.069 satırlık** dengeli (1:1:1 oranına yakın) bir korpus elde edilmiştir.
* **Özellik Çıkarımı:** TF-IDF (Unigram ve Bigram) kullanılmıştır.
* **Modeller:** Destek Vektör Makineleri (SVM), Lojistik Regresyon (LR), Rastgele Orman (RF), Naive Bayes (NB), K-En Yakın Komşu (K-NN) ve Majority Voting (Melez Model).

##  Temel Bulgular
Modeller 5-Fold Cross Validation ile test edilmiş ve aşağıdaki sonuçlar elde edilmiştir:

1. **En Yüksek Başarı:** Sınıf dengesizliği giderildikten sonra, en yüksek F1-Skoru ve Accuracy (%69.5) **Voting Classifier (Melez Model)** ile elde edilmiştir.
2. **Optimizasyon:** GridSearch ile yapılan hiperparametre optimizasyonu ve N-Gram (1,2) denemeleri sonucunda, klasik modellerin bu veri setinde %70 bandında bir tavan performans gösterdiği tespit edilmiştir.
3. **Maliyet/Performans:** Wilcoxon testine göre modeller arası farkın istatistiksel olarak anlamlı olmadığı (p>0.05) görülmüş; Lojistik Regresyonun melez modele kıyasla çok daha kısa sürede (3 saniye) benzer başarıyı vermesiyle en verimli model olduğu kanıtlanmıştır.

##  Dosya Yapısı
* `notebooks/`: Veri temizleme, model eğitimi ve analizleri içeren Jupyter Notebook dosyaları.
* `data/`: Projede kullanılan veri setleri.
