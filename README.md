# 🌴 Dashboard Canne à Sucre — La Réunion

[![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Plotly](https://img.shields.io/badge/Plotly-2.27-3F4F75?style=for-the-badge&logo=plotly&logoColor=white)](https://plotly.com/javascript/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.30%2B-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)](https://streamlit.io/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](https://opensource.org/licenses/MIT)
[![Made in La Réunion](https://img.shields.io/badge/Made%20in-La%20R%C3%A9union-2E8B57?style=for-the-badge&logo=leaflet&logoColor=white)](#)

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
git clone https://github.com/votre-utilisateur/dashboard-canne-reunion.git
cd dashboard-canne-reunion

# 2. Créer un environnement virtuel
python3 -m venv venv
source venv/bin/activate   # Linux/macOS
# ou
venv\Scripts\activate      # Windows

# 3. Installer les dépendances
pip install -r requirements.txt

# 4. Lancer le script
python3 sc.py

# 5. Ouvrir le dashboard
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
dashboard-canne-reunion/
├── sc.py                           # Script principal Python
├── dashboard_canne_reunion.html    # Dashboard généré (autonome)
├── requirements.txt                # Dépendances Python
├── README.md                       # Ce fichier
├── LICENSE                         # Licence MIT
└── cirad_cache/                    # Cache des datasets CIRAD (optionnel)
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
import re
html = open('dashboard_canne_reunion.html').read()
data = re.search(r'const AGRICULTURE = (\[.*?\]);', html, re.DOTALL)
import json
records = json.loads(data.group(1))
print(f'{len(records)} années chargées')
print(f'Première : {records[0][\"annee\"]}')
print(f'Dernière : {records[-1][\"annee\"]}')
"
```

---

## 🛠️ Personnalisation

### Ajouter une année

Dans `aggregate_agricultural_data()`, modifiez la plage :

```python
for year in range(2000, 2026):  # au lieu de 2025
```

### Ajouter un événement à la frise

Dans `get_timeline_events()`, ajoutez une entrée :

```python
{"annee": 2026, "titre": "Votre événement", "type": "politique",
 "description": "Description détaillée..."},
```

Types disponibles : `histoire`, `politique`, `economie`, `climat`,
`recherche`, `energie`, `institution`.

### Ajouter un graphique

1. Ajoutez une div dans le template HTML :
   ```html
   <div class="chart-card"><h3>Titre</h3><div id="chartNouveau" class="plot"></div></div>
   ```

2. Créez une fonction `renderNouveauChart()` en JS

3. Appelez-la dans `init()` et `updateAllCharts()`

---

## 🐛 Dépannage

| Erreur | Solution |
|--------|----------|
| `KeyError: ' box-sizing'` | Utilisez `.replace("__TOKEN__", val)` au lieu de `.format()` |
| `Object of type Timestamp is not JSON serializable` | Utilisez `df_to_json_records()` |
| `400 Client Error` Dataverse | Ajoutez le préfixe `doi:` devant l'identifiant |
| Graphiques non affichés | Vérifiez votre connexion internet (CDN Plotly) |

---

## 🗺️ Roadmap

- [x] Dashboard 2000-2024 complet
- [x] Frise chronologique interactive
- [x] Sélecteur d'année synchronisé
- [ ] Connexion API Météo-France réelle
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

**Votre Nom**
- GitHub : [@votre-utilisateur](https://github.com/votre-utilisateur)
- Email : votre.email@example.com

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

[![GitHub stars](https://img.shields.io/github/stars/votre-utilisateur/dashboard-canne-reunion?style=social)](https://github.com/votre-utilisateur/dashboard-canne-reunion)
[![GitHub forks](https://img.shields.io/github/forks/votre-utilisateur/dashboard-canne-reunion?style=social)](https://github.com/votre-utilisateur/dashboard-canne-reunion/fork)

</div>
