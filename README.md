# 🏥 Healthcare Patient Data Analysis

Uçtan uca bir veri bilimi projesi — keşifsel veri analizi (EDA) ve makine öğrenmesi ile hasta verilerinden içgörü çıkarma.

---

## 📌 Proje Özeti

Bu projede Kaggle'daki [Healthcare Dataset](https://www.kaggle.com/datasets/prasad22/healthcare-dataset) kullanılarak hastane hasta kayıtları analiz edildi. Veri keşfinden model karşılaştırmasına kadar uçtan uca bir pipeline oluşturuldu.

**Hedef:** `Test Results` kolonunu tahmin etmek (Abnormal / Inconclusive / Normal)

---

## 🗂️ Proje Aşamaları

### Aşama 1 — Veri Keşfi
- 55.500 satır, 15 kolon
- Eksik değer yok
- Negatif fatura anomalisi tespit edildi (%0.19)
- Hedef değişken dengeli dağılım: %33 / %33 / %33

### Aşama 2 — Keşifsel Veri Analizi (EDA)
- Yaş & hastalık ilişkisi
- Fatura tutarı analizi (yatış tipi, hastalık, sigorta)
- Hastanede kalış süresi dağılımı
- Zaman serisi analizi
- Korelasyon matrisi

### Aşama 3 — Feature Engineering & Preprocessing
- Yüksek kardinaliteli kolonlar çıkarıldı (`Name`, `Doctor`, `Hospital`)
- Kategorik kolonlar Label Encoding ile sayıya çevrildi
- Yeni feature türetildi: `Length of Stay`
- Train/Test split: %80 / %20
- StandardScaler ile ölçeklendirme

### Aşama 4 — ML Modelleme
- Random Forest Classifier
- XGBoost Classifier
- Confusion Matrix karşılaştırması
- Feature Importance analizi

---

## 📊 Model Sonuçları

| Model | Accuracy |
|---|---|
| Random Forest | %44 |
| XGBoost | %38 |

---

## 🔍 Önemli Bulgu

Proje sürecinde veri setinin **sentetik (yapay) üretilmiş** olduğu tespit edildi:

- Tüm kategorik değişkenler neredeyse mükemmel dengeli dağılım gösteriyor
- İsim kolonunda rastgele büyük/küçük harf karışımı (`DAvId muNoZ`)
- Hastalıklar yaş gruplarına göre eşit dağılmış — gerçekte olmaz
- `Test Results` ile diğer değişkenler arasında anlamlı bir ilişki yok

Bu nedenle model %44 accuracy verdi. **Gerçek hasta verisinde** feature'lar arasında anlamlı ilişkiler olacağından bu skorun %75-85 bandına çıkması beklenir. Veri kalitesinin model performansından daha belirleyici olduğu bu proje ile somut olarak gözlemlendi.

---

## 🛠️ Kullanılan Teknolojiler

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Pandas](https://img.shields.io/badge/Pandas-2.0-green)
![Scikit--learn](https://img.shields.io/badge/Scikit--learn-1.3-orange)
![XGBoost](https://img.shields.io/badge/XGBoost-1.7-red)
![Seaborn](https://img.shields.io/badge/Seaborn-0.12-purple)

- **Pandas** — veri manipülasyonu
- **Matplotlib / Seaborn** — görselleştirme
- **Scikit-learn** — preprocessing ve Random Forest
- **XGBoost** — gradient boosting modeli

---

## 📁 Dosya Yapısı

```
├── healthcare_analysis.ipynb     # Tüm proje tek notebook içinde
└── README.md                     # Proje açıklaması
```

---

## 🚀 Nasıl Çalıştırılır?

1. [Kaggle Dataset](https://www.kaggle.com/datasets/prasad22/healthcare-dataset) sayfasından veriyi indir
2. Notebook'ları sırayla çalıştır
3. Kaggle ortamında çalıştırıyorsan path `/kaggle/input/healthcare-dataset/healthcare_dataset.csv`

---

## 💡 Sonraki Adımlar

- Gerçek hasta verisi ile modeli test etmek
- Hyperparameter tuning ile model optimizasyonu
- LightGBM ve Logistic Regression karşılaştırması
- SHAP değerleri ile model yorumlanabilirliği

---

*Bu proje öğrenme amaçlı yapılmıştır.*

