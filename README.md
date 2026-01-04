# Détection des anomalies dans les transactions bancaires
Ce projet de Machine Learning a été élaboré en Juillet 2025 mais publié en Décembre 2025 dans un cadre de mise à jour d'un portfolio personnel.

## 📌 Contexte
Ce projet vise à détecter des anomalies (fraudes) dans des transactions bancaires à partir d’un dataset réel issu de Kaggle.
Nous utilisons des approches :
- **Supervisées** : modèles de classification (ex : Logistic Regression, Random Forest, SVM, etc.)
- **Non supervisées** : méthodes de détection d’anomalies (**Isolation Forest**, **LOF**)

---

## 📂 Dataset
Dataset Kaggle officiel :  
🔗 https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud

Page "Data" :  
🔗 https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud/data


---

## ⬇️ Télécharger le dataset (méthode recommandée)

### Télécharger manuellement
Télécharger depuis Kaggle :
https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud/data

Puis placer le fichier dans :
`data/creditcard.csv`

---

## 📒 Notebooks inclus
Les notebooks disponibles dans le dossier `notebooks/` :
- Statistiques descriptives + Visualisation + Modèles supervisés
- Apprentissage non supervisé : Isolation Forest
- Isolation Forest : tests paramètres
- Apprentissage non supervisé : LOF

---

## 📦 Installation
Créer un environnement virtuel (optionnel mais recommandé) :

```bash
python -m venv venv
source venv/bin/activate   # Linux/Mac
venv\Scripts\activate      # Windows
```

Installer les dépendances :

```bash
pip install -r requirements.txt
```

---

## ▶️ Exécution
Lancer Jupyter Notebook :

```bash
jupyter notebook
```

ou ouvrir sur Google Colab.
---

## 📊 Résultats (extraits des notebooks)

### 1) Modèles supervisés (classification)
Sur le notebook **Statistique descriptive & Visualisation & Modèles supervisés**, plusieurs modèles ont été entraînés.
Les meilleurs résultats observés (ordre de grandeur) sur le dataset déséquilibré sont :

- **Accuracy ≈ 0.9995 – 0.9996**
- **AUC-ROC jusqu’à ≈ 0.9584**
- Exemples de métriques relevées :
  - Recall ≈ **0.7158**, Precision ≈ **0.9577**, F1 ≈ **0.8193**, AUC-ROC ≈ **0.9404**
  - Recall ≈ **0.7579**, Precision ≈ **0.9114**, F1 ≈ **0.8276**, AUC-ROC ≈ **0.9584**
  - Recall ≈ **76.84%**, Precision ≈ **96.05%** (meilleure combinaison précision/rappel dans les sorties)

📌 Remarque : la classe fraude est très minoritaire, donc **Recall/F1/AUC-ROC** sont plus pertinents que l’accuracy seule.

### 2) Isolation Forest (non supervisé)
Sur le notebook **Isolation Forest**, la matrice de confusion obtenue est :

- TN = 282 613  
- FP = 640  
- FN = 261  
- TP = 212  

Ce qui donne environ :
- **Precision ≈ 0.249**
- **Recall ≈ 0.448**
- **F1-score ≈ 0.320**

➡️ Isolation Forest détecte une partie des fraudes mais produit encore pas mal de faux positifs.

### 3) Isolation Forest — Test de paramètres
Sur le notebook **Isolation Forest (test paramètres)**, plusieurs configurations ont été comparées.
Le meilleur F1-score observé dans les sorties est autour de :

- **F1-score ≈ 0.3562**  
avec un compromis :
- Recall ≈ **0.4989**
- Precision ≈ **0.2770**

➡️ L’ajustement des paramètres améliore légèrement le compromis recall/precision.

### 4) LOF (Local Outlier Factor)
Sur le notebook **LOF**, les résultats affichés montrent :

- True Positives ≈ 28
- False Positives ≈ 824
- **Precision ≈ 0.0329**
- **F1-score ≈ 0.0423**

➡️ Dans cette configuration, LOF génère trop de faux positifs et reste moins performant que Isolation Forest.

---

## 🧑‍💻 Auteur
**ANDRIANJARA Jacob Rino**  
Projet académique : Détection des anomalies dans les transactions bancaires
