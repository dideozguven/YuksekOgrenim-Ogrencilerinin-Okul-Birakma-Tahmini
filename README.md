# 🎓 Öğrenci Başarı Tahmini: Veri Madenciliği ile Modelleme
Bu proje, yükseköğrenim düzeyindeki öğrencilerin akademik başarılarını tahmin etmek amacıyla makine öğrenmesi algoritmaları kullanılarak gerçekleştirilmiştir. Veri madenciliği süreçleri ve farklı sınıflandırma teknikleri ile “Dropout”, “Enrolled” ve “Graduate” olmak üzere üç sınıfta sınıflandırma yapılmıştır.

## 📌 **Proje Amacı**

Eğitim hayatında öğrencilerin başarısını erken safhada tahmin ederek:

- Riskli öğrencilerin tespit edilmesi,

- Rehberlik ve destek süreçlerinin iyileştirilmesi,

- Eğitim kurumlarının karar destek sistemlerine katkı sağlanması hedeflenmiştir.

## 🧠Kullanılan Yöntemler

Makine Öğrenmesi Algoritmaları:

- Decision Tree

- Random Forest

- XGBoost

## Veri Ön İşleme

- Eksik veri kontrolü

- Kategorik verilerin etiketlenmesi (Label Encoding)

- SMOTE ile veri dengeleme

## Performans Değerlendirme

- Doğruluk (Accuracy)

- F1-Score (sınıf bazlı ve ortalama)

- Confusion Matrix

- Güven Aralığı Hesaplamaları (Bootstrap yöntemi)

## 📁 Veri Seti Bilgisi

Bu projede kullanılan veri seti, UCI Machine Learning Repository (https://archive.ics.uci.edu/) üzerinden temin edilmiştir. Toplamda 4424 gözlem ve 37 özellik içeren bu veri seti, öğrencilerin demografik yapıları, akademik geçmişleri ve sosyoekonomik durumlarına ilişkin geniş bir yelpazede bilgi sunmaktadır. Öznitelikler üç ana grupta toplanabilir: Demografik bilgiler (cinsiyet, yaş, uyruk, medeni durum, ebeveyn meslek ve eğitim durumu), akademik bilgiler (üniversiteye giriş notu, önceki eğitim notu, dönemlik ders ve sınav sayıları, ders geçme durumu) ve sosyoekonomik bilgiler (harç ödeme düzeni, burs durumu, borçluluk, işsizlik ve enflasyon oranı). Modelleme sürecinde hedef değişken olarak Target sütunu kullanılmıştır ve bu sütun, öğrencinin akademik durumunu üç farklı sınıfta belirtmektedir: Dropout (okulu bırakmış), Enrolled (kayıtlı) ve Graduate (mezun).


Hedef değişkenin sınıf dağılımına bakıldığında, 2209 öğrenci mezun, 1421 öğrenci okulu bırakmış ve yalnızca 794 öğrenci hâlâ kayıtlı durumdadır. Bu dağılım, sınıflar arasında belirgin bir dengesizlik olduğunu göstermektedir. Özellikle “Enrolled” sınıfı sayıca azınlıkta olduğu için bu sınıfın öğrenilmesi makine öğrenmesi algoritmaları açısından daha zorlayıcı hale gelmektedir. Bu nedenle modelleme sürecinde, sınıf dengesizliğini gidermek amacıyla SMOTE (Synthetic Minority Over-sampling Technique) gibi veri dengeleme teknikleri kullanılmıştır.

## 📊 Veri Keşfi ve Görselleştirme

- Histogramlar ile dağılım analizi

- Boxplot ile sayısal değişkenlerin Target'a göre karşılaştırılması

- Countplot ile kategorik değişkenlerin sınıflara göre dağılımı

- **Öne çıkan bulgular:**

- Gündüz öğretiminde mezuniyet oranı daha yüksek.

- Kadın öğrencilerin başarı oranı erkeklere göre daha fazla.

- Harç ödemelerini düzenli yapanlar mezun olma eğiliminde.

## 🔧 Veri Ön İşleme

- Eksik Veri: Hiçbir değişkende eksik veri bulunmamaktadır.

- Encoding: Hedef değişken sayısallaştırıldı (Graduate=2, Enrolled=1, Dropout=0).

- Dengeleme: SMOTE kullanılarak sınıf dengesizliği giderildi.

## 🤖 Modelleme ve Sonuçlar
### 1. Decision Tree

- Doğruluk (SMOTE ile): %65.5

- Enrolled sınıfı F1-score: %43

- Özellik önemi: En etkili değişken Curricular units 2nd sem (approved)

- Parametre denemeleri: max_depth, criterion varyasyonları ile optimize edildi

### 2. Random Forest

- Doğruluk (SMOTE ile): %73.3

- Enrolled sınıfı F1-score: %50

- Avantajı: Düşük varyans, yüksek genelleme

- Overfitting Testi: Eğitim ve test doğrulukları çok yakındı → overfitting yok

### 3. XGBoost

- Doğruluk (SMOTE ile): %76.5

- Enrolled sınıfı F1-score: %54

- Avantajı: Hem genel doğruluk hem de sınıf bazlı başarıda en yüksek performans

- Güven Aralığı: Bootstrap ile doğruluk oranı [0.7440, 0.7877]

## 📈 Performans Karşılaştırması

Model	Accuracy	F1-Score (0)	F1-Score (1)	F1-Score (2)	Macro Avg	Weighted Avg
Decision Tree + SMOTE	0.6551	0.71	0.43	0.75	0.63	0.68
Random Forest + SMOTE	0.7334	0.72	0.50	0.84	0.69	0.74
XGBoost + SMOTE	0.7651	0.77	0.54	0.85	0.72	0.77

📌 Sonuç: XGBoost modeli, sınıf dengesini koruyarak en yüksek başarıyı göstermiştir.


## 🔬 Teknik Detaylar

- Programlama Dili: Python 3.11

- Kullanılan Kütüphaneler: pandas, numpy, matplotlib, seaborn, sklearn: preprocessing, model_selection, metrics, DecisionTreeClassifier, RandomForestClassifier, xgboost, imblearn: SMOTE

## ✅ Sonuç ve Katkılar

- SMOTE sayesinde sınıf dengesizliği önemli ölçüde giderildi.

- XGBoost modeli hem genel başarıda hem de azınlık sınıflarda güçlü sonuçlar verdi.

- Bootstrap yöntemi ile model güvenilirliği istatistiksel olarak ispatlandı.
## Youtube Video Linki

Projenin detaylı anlatıldığı video için: https://youtu.be/gFA8yxTr-dc

## 📌 Gelecek Çalışmalar

- CatBoost, LightGBM gibi alternatif modeller ile karşılaştırmalar yapılabilir.

- Özellik seçimi (feature selection) algoritmaları ile model sadeleştirilebilir.

- Weka veya AutoML platformlarıyla modelleme tekrarlanabilir.

Proje Sahibi:

Fatma Didenur Özgüven

Veri Madenciliğine Giriş – 2024-2025 Bahar Dönemi

Bursa Teknik Üniversitesi
