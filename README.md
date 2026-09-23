# 🌴 Dashboard Canne à Sucre — La Réunion

[![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Plotly](https://img.shields.io/badge/Plotly-2.27-3F4F75?style=for-the-badge&logo=plotly&logoColor=white)](https://plotly.com/javascript/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.30%2B-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)](https://streamlit.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![Made in La Réunion](https://img.shields.io/badge/Made%20in-La%20R%C3%A9union-2E8B57?style=for-the-badge)](#)

[![CIRAD Dataverse](https://img.shields.io/badge/Data-CIRAD%20Dataverse-0055A4?style=for-the-badge)](https://dataverse.cirad.fr/)
[![ODEADOM](https://img.shields.io/badge/Data-ODEADOM-2E8B57?style=for-the-badge)](https://www.odeadom.fr/)
[![Météo-France](https://img.shields.io/badge/Data-M%C3%A9t%C3%A9o--France-00478F?style=for-the-badge)](https://portail-api.meteofrance.fr/)
[![Observatoire Énergie Réunion](https://img.shields.io/badge/Data-OER-FF6B00?style=for-the-badge)](https://www.observatoire-energie-reunion.fr/)

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)](#)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)](#)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)](#)
[![Pandas](https://img.shields.io/badge/Pandas-2.0-150458?style=flat-square&logo=pandas&logoColor=white)](#)
[![NumPy](https://img.shields.io/badge/NumPy-1.24-013243?style=flat-square&logo=numpy&logoColor=white)](#)

> **Dashboard analytique complet** de la filière canne à sucre à La Réunion : 25 ans de données historiques, 18 graphiques interactifs, frise chronologique et projections climatiques jusqu'en 2090.

---

## 📊 Aperçu

| Section | Contenu |
|---------|---------|
| 📈 **Métriques clés** | 6 KPIs dynamiques (production, rendement, surface, électricité, valeur, emplois) |
| 📊 **Production & Économie** | Évolution 2000-2024, rendement vs surface, waterfall, répartition des sucres |
| ⚡ **Énergie & Bagasse** | Production bagasse + pellets, électricité renouvelable |
| 🌱 **Agronomie** | Systèmes économes en herbicides (CanécoH V2), IFT, climat |
| 🗺️ **Cartographie** | Treemap communes, bassins de production, emplois |
| 🌤️ **Météo** | Températures, précipitations |
| 🔮 **Projections** | Modèle MOSICAS (RCP 2.6 / 4.5 / 8.5) jusqu'en 2090 |
| 🕰️ **Frise interactive** | 23 événements historiques (1810-2025) |

---

## ✨ Fonctionnalités

- 🎛️ **Sélecteur d'année interactif** — Slider 2000-2024 + 8 boutons rapides
- 🕰️ **Frise chronologique** — Clic sur un événement pour filtrer tous les graphiques
- 📌 **Marqueur de sélection** — Point rouge cerclé sur chaque graphique indiquant l'année active
- 📋 **Panneau détail** — 16 indicateurs par année sélectionnée
- 🌐 **HTML autonome** — Aucun serveur requis, ouvrable directement dans le navigateur
- 📱 **Responsive** — Adapté mobile, tablette et desktop
- 🎨 **Plotly.js** — Graphiques interactifs (zoom, pan, export PNG)

---

## 🚀 Installation

### Prérequis

- Python **3.9+**
- pip

### Étapes

```bash
# 1. Cloner le dépôt
git clone https://github.com/gunout/Dashboard-Cannes-Productions-Reunion.git
cd Dashboard-Cannes-Productions-Reunion

# 2. Créer un environnement virtuel
python3 -m venv venv
source venv/bin/activate   # Linux/macOS
# ou
venv\Scripts\activate      # Windows

# 3. Installer les dépendances
pip install -r requirements.txt

# 4. Lancer le script principal
python3 sc.py

# 5. Ouvrir le dashboard généré
open dashboard_canne_reunion.html      # macOS
xdg-open dashboard_canne_reunion.html  # Linux
start dashboard_canne_reunion.html     # Windows
```

---

## 📦 Dépendances

```txt
requests>=2.31.0
pandas>=2.0.0
numpy>=1.24.0
plotly>=5.18.0
```

---

## 📁 Structure du projet

```
Dashboard-Cannes-Productions-Reunion/
├── sc.py                           # Script principal Python (téléchargement + génération HTML)
├── dashboard_canne_reunion.html    # Dashboard généré (autonome, 18 graphiques)
├── requirements.txt                # Dépendances Python
├── README.md                       # Ce fichier
├── LICENSE                         # Licence MIT
└── cirad_cache/                    # Cache des datasets CIRAD (optionnel)
```

---

## 🐍 Le script `sc.py`

Le script `sc.py` est le cœur du projet. Il exécute les 6 étapes suivantes :

| Étape | Fonction | Description |
|-------|----------|-------------|
| **1/6** | `download_cirad_dataset()` | Télécharge les 5 datasets depuis le CIRAD Dataverse via l'API `/api/datasets/:persistentId/` (préfixe `doi:` obligatoire) |
| **2/6** | `download_meteo_data()` | Récupère les données météo de la station Saint-Denis Gillot (97418001) |
| **3/6** | `aggregate_agricultural_data()` | Agrège les données annuelles 2000-2024 (production, sucre, rhum, bagasse, IFT, climat, emplois) |
| **4/6** | `aggregate_extended_data()` | Charge les données étendues (bagasse OER, pellets, CanécoH V2, BSV, MOSICAS, bassins, sucres, emplois, subventions) |
| **5/6** | `get_timeline_events()` | Charge les 23 événements de la frise chronologique (1810-2025) |
| **6/6** | `generate_html_with_data()` | Génère le HTML autonome avec injection JSON via `.replace("__TOKEN__", valeur)` |

### Points techniques clés

- **Sérialisation JSON-safe** : la fonction `df_to_json_records()` convertit les `Timestamp` pandas en `str` et les types numpy (`int64`, `float64`) en types Python natifs — évite l'erreur `Object of type Timestamp is not JSON serializable`.
- **Injection par tokens** : le template HTML utilise `__AGRICULTURE_DATA__`, `__COMMUNE_DATA__`, etc. — évite le `KeyError: ' box-sizing'` causé par `.format()` sur du CSS.
- **Préfixe `doi:`** : obligatoire pour l'API Dataverse (sans lui : `400 Client Error`).
- **Encodage UTF-8** : `output_path.write_text(html_content, encoding='utf-8')` — évite les problèmes d'accents réunionnais.

### Exécution typique

```
============================================================
Dashboard Canne à Sucre - Version enrichie
============================================================

[1/6] Téléchargement des datasets CIRAD Dataverse...
  - canne_cover_crops_1: doi:10.18167/DVN1/SLGV2M
    ✓ 5 fichier(s) — Experimental dataset on the use of cover crops...
  - canne_cover_crops_2: doi:10.18167/DVN1/WTFBBY
    ✓ 5 fichier(s) — Experimental dataset on the use of cover crops...
  ...

[2/6] Récupération des données météo...
    ✓ 366 jours

[3/6] Agrégation des données agricoles annuelles...
    ✓ 25 années (2000-2024)
    ✓ 12 communes

[4/6] Agrégation des données étendues...
    ✓ bagasse : 9 lignes
    ✓ pellets : 2 lignes
    ✓ canecoh : 3 systèmes
    ✓ bsv : 10 parcelles
    ✓ mosicas : 8 projections
    ✓ bassins : 5 bassins
    ✓ sucres : 3 types
    ✓ emplois : 4 catégories
    ✓ subventions : 5 années

[5/6] Chargement de la frise chronologique...
    ✓ 23 événements historiques

[6/6] Génération du HTML...
    ✓ Fichier : dashboard_canne_reunion.html

============================================================
✅ Terminé ! Ouvrez le fichier HTML dans votre navigateur.
============================================================
```

---

## 🔄 Pipeline des données

```
┌─────────────────────┐
│  Sources externes   │
│  • CIRAD Dataverse  │
│  • ODEADOM / DAAF   │
│  • Observatoire É.  │
│  • Météo-France     │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│  sc.py              │
│  • Téléchargement   │
│  • Agrégation       │
│  • Sérialisation    │
└──────────┬──────────┘
           │
           ▼
┌─────────────────────┐
│  HTML autonome      │
│  • Plotly.js        │
│  • JSON injecté     │
│  • Interactions     │
└─────────────────────┘
```

---

## 📚 Sources de données

| Source | Type | URL |
|--------|------|-----|
| **CIRAD Dataverse** | Datasets expérimentaux | [dataverse.cirad.fr](https://dataverse.cirad.fr/) |
| **ODEADOM** | Production, surfaces, prix | [odeadom.fr](https://www.odeadom.fr/) |
| **DAAF Réunion** | Atlas agricole, pesticides | [daaf.reunion.agriculture.gouv.fr](https://daaf.reunion.agriculture.gouv.fr/) |
| **Observatoire Énergie Réunion** | Bagasse, pellets | [observatoire-energie-reunion.fr](https://www.observatoire-energie-reunion.fr/) |
| **Météo-France** | Climat, prévisions | [portail-api.meteofrance.fr](https://portail-api.meteofrance.fr/) |
| **BSV Canne** | Suivi phytosanitaire | [bsv-reunion.fr](https://bsv-reunion.fr/) |
| **EGC** | États Généraux de la Canne | — |

---

## 🧪 Vérifications

```bash
# Vérifier que le HTML a bien été généré
ls -lh dashboard_canne_reunion.html

# Vérifier la validité JSON des données injectées
python3 -c "
import re, json
html = open('dashboard_canne_reunion.html').read()
data = re.search(r'const AGRICULTURE = (\[.*?\]);', html, re.DOTALL)
records = json.loads(data.group(1))
print(f'{len(records)} années chargées')
print(f'Première : {records[0][\"annee\"]}')
print(f'Dernière : {records[-1][\"annee\"]}')
"
```

---

## 🛠️ Personnalisation

### Ajouter une année

Dans `sc.py`, fonction `aggregate_agricultural_data()` :

```python
for year in range(2000, 2026):  # au lieu de range(2000, 2025)
```

### Ajouter un événement à la frise

Dans `sc.py`, fonction `get_timeline_events()`, ajoutez une entrée :

```python
{"annee": 2026, "titre": "Votre événement", "type": "politique",
 "description": "Description détaillée..."},
```

Types disponibles : `histoire`, `politique`, `economie`, `climat`, `recherche`, `energie`, `institution`.

### Ajouter un graphique

1. Ajoutez une div dans le template HTML de `sc.py` :
   ```html
   <div class="chart-card"><h3>Titre</h3><div id="chartNouveau" class="plot"></div></div>
   ```

2. Créez une fonction `renderNouveauChart()` en JS (dans le même template)

3. Appelez-la dans `init()` et `updateAllCharts()`

---

## 🐛 Dépannage

| Erreur | Solution |
|--------|----------|
| `KeyError: ' box-sizing'` | Utilisez `.replace("__TOKEN__", val)` au lieu de `.format()` dans `sc.py` |
| `Object of type Timestamp is not JSON serializable` | Utilisez `df_to_json_records()` avant `json.dumps()` |
| `400 Client Error` Dataverse | Ajoutez le préfixe `doi:` devant l'identifiant du dataset |
| Graphiques non affichés | Vérifiez votre connexion internet (CDN Plotly : `cdn.plot.ly`) |
| Accents cassés dans le HTML | Vérifiez `encoding='utf-8'` dans `write_text()` |

---

## 🗺️ Roadmap

- [x] Dashboard 2000-2024 complet
- [x] Frise chronologique interactive (23 événements)
- [x] Sélecteur d'année synchronisé
- [x] Script `sc.py` autonome (téléchargement + génération HTML)
- [ ] Connexion API Météo-France réelle (clé API requise)
- [ ] Carte Leaflet avec parcelles géolocalisées
- [ ] Export PDF automatique
- [ ] Extension aux autres DROM (Guadeloupe, Martinique, Guyane, Mayotte)
- [ ] Système d'alertes email
- [ ] Base de données historique (SQLite/DuckDB)

---

## 🤝 Contribution

Les contributions sont bienvenues !

```bash
# 1. Fork
# 2. Créer une branche
git checkout -b feature/ma-fonctionnalite

# 3. Commit
git commit -m "feat: ajout de ma fonctionnalité"

# 4. Push
git push origin feature/ma-fonctionnalite

# 5. Ouvrir une Pull Request
```

---

## 📄 Licence

Ce projet est sous licence **MIT** — voir le fichier [LICENSE](LICENSE) pour plus de détails.

---

## 👤 Auteur

**gunout**
- GitHub : [@gunout](https://github.com/gunout)
- Dépôt : [Dashboard-Cannes-Productions-Reunion](https://github.com/gunout/Dashboard-Cannes-Productions-Reunion)

---

## 📖 Références

### Datasets CIRAD Dataverse

Les 5 datasets suivants sont téléchargés par `sc.py` via l'API Dataverse :

1. **Canne cover crops 1** — DOI : [`10.18167/DVN1/SLGV2M`](https://doi.org/10.18167/DVN1/SLGV2M)
   - *Experimental dataset on the use of cover crops for weed control in sugarcane at La Réunion*
2. **Canne cover crops 2** — DOI : [`10.18167/DVN1/WTFBBY`](https://doi.org/10.18167/DVN1/WTFBBY)
3. **Canne cover crops 3** — DOI : [`10.18167/DVN1/1S0YSQ`](https://doi.org/10.18167/DVN1/1S0YSQ)
4. **Canne cover crops 4** — DOI : [`10.18167/DVN1/YUKJGB`](https://doi.org/10.18167/DVN1/YUKJGB)
5. **Canne cover crops 5** — DOI : [`10.18167/DVN1/CLOJLC`](https://doi.org/10.18167/DVN1/CLOJLC)

### Publications scientifiques et rapports

- **Christina, M. et al. (2025)** — *Modélisation des rendements canniers à La Réunion sous scénarios climatiques RCP 2.6, 4.5 et 8.5 (2002-2100)*. CIRAD / eRcane. Modèle MOSICAS.
- **Chetty, J. et al. (2026)** — *CanécoH V2 : évaluation de systèmes économes en herbicides à La Réunion*. CIRAD / eRcane.
- **DAAF Réunion (2024)** — *Atlas agricole de La Réunion*. Direction de l'Alimentation, de l'Agriculture et de la Forêt.
- **DAAF Réunion (2022)** — *Enquête sur les pratiques culturales de la canne à sucre*. Agreste.
- **BSV Canne à sucre (2026)** — *Bulletin de Santé du Végétal, janvier-mars 2026*. 10 parcelles sur 9 communes.
- **États Généraux de la Canne (2025)** — *Bilan et perspectives de la filière canne à La Réunion*.

### Sources institutionnelles

- **ODEADOM** — *Statistiques de production 2024*. Office de Développement de l'Économie Agricole des DOM.
- **Observatoire Énergie Réunion (2024)** — *Production électrique à partir de bagasse et pellets*. OER.
- **Albioma (2024)** — *Conversion 100% biomasse des centrales de Bois-Rouge et Le Gol*.
- **Météo-France** — *API Ciblée Clim pour La Réunion*. [portail-api.meteofrance.fr](https://portail-api.meteofrance.fr/)
- **eRcane** — Centre de recherche et d'innovation sur la canne à sucre à La Réunion.

### Documentation technique

- [API Dataverse](https://guides.dataverse.org/en/latest/api/) — Guide officiel pour l'accès aux datasets
- [Plotly.js](https://plotly.com/javascript/) — Bibliothèque de graphiques utilisée dans le dashboard
- [Pandas](https://pandas.pydata.org/docs/) — Manipulation des DataFrames
- [Streamlit](https://docs.streamlit.io/) — Framework utilisé pour la version initiale

### Données historiques de référence

- Production 2022 : **1 436 226 t** (ODEADOM, après cyclone Batsirai)
- Production 2024 : **1 137 720 t** (ODEADOM, après cyclone Garance)
- Bagasse 2024 : **174,1 GWh** et **379 067,6 t** (OER)
- Pellets 2024 : **547 290 t** → **710,9 GWh** (OER)
- Emplois filière : **18 300** (soit 12,5% de l'emploi privé réunionnais)

---

## 🙏 Remerciements

- **CIRAD** et **eRcane** pour les datasets ouverts
- **ODEADOM**, **DAAF Réunion**, **Chambre d'Agriculture** pour les données de référence
- **Observatoire Énergie Réunion** pour les données bagasse/pellets
- **Météo-France** pour l'API climatologique
- **Plotly** pour la bibliothèque de graphiques

---

## ⭐ Soutenir le projet

Si ce dashboard vous est utile, n'hésitez pas à :

- ⭐ Mettre une **étoile** sur GitHub
- 🐛 Signaler les **bugs** dans les Issues
- 💡 Proposer des **améliorations** via Pull Request
- 📢 **Partager** le projet autour de vous

---

<div align="center">

**🌴 Fait avec ❤️ à La Réunion 🌴**

[![GitHub stars](https://img.shields.io/github/stars/gunout/Dashboard-Cannes-Productions-Reunion?style=social)](https://github.com/gunout/Dashboard-Cannes-Productions-Reunion)
[![GitHub forks](https://img.shields.io/github/forks/gunout/Dashboard-Cannes-Productions-Reunion?style=social)](https://github.com/gunout/Dashboard-Cannes-Productions-Reunion/fork)

</div>
