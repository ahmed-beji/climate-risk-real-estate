# 🌍 Impact du Dérèglement Climatique sur les Prix Immobiliers : Le Marché est-il Rationnel ?


> **Projet Statistique de 2ème année - École Nationale de la Statistique et de l'Analyse de l'Information (ENSAI)**
> *Évaluation de l'efficience informationnelle du marché immobilier résidentiel français face à l'accélération des chocs climatiques.*

## 📑 Synthèse du Projet
Ce projet de recherche appliquée en économétrie spatiale et Data Science évalue comment le marché immobilier français tarife le risque climatique (inondations, sécheresse/RGA, risques marins). À l'aide d'un panel macro-spatial de plus de 113 000 observations (2021-2024), nous démontrons que le signal-prix du danger est systématiquement parasité par la tension foncière et les aménités environnementales (biais héliotropique, paradoxe littoral).

## 🚀 Résultats Empiriques & Insights
Notre modélisation déconstruit l'estimateur national et met en évidence une **asymétrie comportementale** frappante :

* **Le marché réagit au flux, pas au stock :** L'historique des catastrophes (mémoire longue) n'est pas tarifé. Le marché réagit uniquement au **choc informationnel** (rupture de tendance et aggravation récente de la sinistralité).
* **Rationalité Institutionnalisée (Appartements) :** L'habitat collectif sanctionne rationnellement l'aggravation des inondations (**décote de -2,78%**), le cadre de la copropriété imposant une visibilité financière du risque via les charges d'entretien.
* **Le Biais d'Aménité (Maisons) :** Le marché individuel échoue à évaluer sa vulnérabilité géotechnique. L'attrait pour le cadre de vie génère une prime paradoxale (**+5,33%**) qui annule la perception du danger.
* **Non-Stationnarité Spatiale :** La tarification du risque dépend de la liquidité locale. Le marché hyper-tendu du Var panique face au risque (**décote de -12,24%**), tandis que le marché rural détendu de la Creuse survalorise l'aménité (**prime de +27,78%**).

## 🛠️ Stack Technique & Pipeline de Données

Le projet couvre l'intégralité du cycle de vie de la donnée, de l'extraction à l'inférence causale.

### Ingénierie des Données
* **DVF (Demandes de Valeurs Foncières) :** Nettoyage, trimming des valeurs aberrantes et agrégation spatio-temporelle de 4,6 millions de transactions brutes.
* **GASPAR :** Feature engineering pour construire des indicateurs de vulnérabilité dynamiques (fenêtres glissantes, calcul de dérivées discrètes d'aggravation avec application de seuils).
* **FiLoSoFi :** Contrôle des biais socio-économiques géographiques via l'intégration du revenu médian.

### Modélisation Économétrique
* Modèles de **Prix Hédoniques** (théorie de Rosen).
* **Régression en Panel (WLS / OLS) avec Effets Fixes** bidirectionnels (départementaux et annuels) pour purger les biais de variables omises.
* **Erreurs Standards Clusterisées** au niveau départemental pour corriger l'hétéroscédasticité et l'autocorrélation spatiale.

### Outils & Librairies
* `pandas`, `numpy` (Manipulation et nettoyage de données massives)
* `statsmodels`, `linearmodels` (Modélisation économétrique et données de panel)
* `folium`, `branca` (Cartographie interactive, Heatmaps et clusters spatiaux)

## 📂 Architecture du Dépôt
'''
PROJ_STAT/
├── data/
├── notebooks/
│   ├── 01_nettoyage_dvf_gaspar.ipynb
│   ├── 02_modele_hedonique.ipynb
│   └── 03_creation_carte_interactive.ipynb
├── output/
│   └── carte_interactive_finale.html
├── src/
├── venv/
├── .gitignore
├── Rapport_final.pdf
└── README.md
'''