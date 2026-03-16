# Détection de Fraude par Carte Bancaire

Ce projet porte sur la détection de transactions frauduleuses à partir de données réelles de cartes bancaires.

J'ai construit un pipeline complet : exploration des données, entraînement de modèles Machine Learning, analyse des résultats, et création d'un tableau de bord Power BI pour visualiser les fraudes détectées.

---

## Le problème

Sur 284 807 transactions, seulement 492 sont des fraudes — soit 0,17 %. C'est très peu, et c'est justement ce qui rend le problème difficile : un modèle basique qui prédit toujours "normal" aurait 99,83 % de précision... mais ne détecterait aucune fraude.

L'objectif était donc de construire un modèle qui détecte vraiment les fraudes, pas juste un modèle qui a l'air bon sur le papier.

---

## Ce que j'ai fait

**1. Exploration des données**
J'ai analysé la distribution des montants, visualisé le déséquilibre entre fraudes et transactions normales, et confirmé que le montant seul ne suffit pas à détecter une fraude.

**2. Préparation**
- Séparation des données : 80 % pour entraîner, 20 % pour tester
- Normalisation du montant
- Configuration des modèles pour tenir compte du déséquilibre des classes

**3. Deux modèles testés**
- **Régression Logistique** — simple et interprétable, utilisée comme référence
- **XGBoost** — plus performant sur ce type de données déséquilibrées

**4. Résultats avec XGBoost**
- 85 fraudes détectées sur 98 — soit 87 % de recall
- Seulement 36 fausses alertes sur 56 864 transactions normales
- PR-AUC : 0.87 — ROC-AUC : 0.98

**5. Explicabilité avec SHAP**
J'ai utilisé SHAP pour comprendre quelles variables influencent le plus les prédictions. La variable V14 est la plus déterminante — ce sont des comportements transactionnels complexes, pas le montant, qui trahissent une fraude.

**6. Tableau de bord Power BI**
J'ai exporté les résultats vers Power BI pour créer un dashboard interactif. On peut filtrer par niveau de risque, explorer chaque transaction suspecte, et suivre les KPIs clés.

---

## Stack utilisée

- Python — Pandas, NumPy, Scikit-learn, XGBoost, SHAP, Matplotlib, Seaborn
- Google Colab
- Power BI

---

## Dataset

Source : [Kaggle — Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)

Le fichier `creditcard.csv` n'est pas inclus dans ce repo (trop lourd). Télécharge-le directement depuis Kaggle et place-le à la racine du projet avant de lancer le notebook.

[📥 Télécharger le fichier Power BI (.pbix)]([colle-ton-lien-ici](https://colab.research.google.com/drive/14qzfpYzGZ9zpJp6XwHrDr5PSiDmWSnxh?usp=drive_link)

---

## Me contacter

[LinkedIn — Zohair EZZOUINE](https://linkedin.com/in/zohair-ezzouine)
