# 📊 ESG Template Automation — InnovTech SA

Génération automatique de rapports ESG à partir d'une base de données Excel, avec envoi par email. Propulsé par Python et n8n.

---

## 🚀 Comment ça marche

1. n8n se déclenche chaque matin à **8h00**
2. Il appelle l'API Python hébergée sur Render
3. L'API lit la base de données Excel, génère le rapport ESG
4. Le rapport est envoyé automatiquement par email en pièce jointe

---

## 🗂️ Fichiers

| Fichier | Rôle |
|--------|------|
| `api_esg.py` | API Python — génère le rapport et envoie l'email |
| `generer_rapport_esg.py` | Script manuel — génère le rapport sans automatisation |
| `InnovTech_Base_Donnees.xlsx` | Base de données source |
| `ESG_Template_TotalEnergies_STRUCTURED.xlsx` | Template du rapport ESG |
| `requirements.txt` | Dépendances Python |
| `n8n_workflow_esg_v3.json` | Workflow n8n à importer |

---

## ⚙️ Installation

### 1. Cloner le repo
```bash
git clone https://github.com/azizamara745-glitch/ESG-TEMPLATE-AUTOMATION.git
cd ESG-TEMPLATE-AUTOMATION
```

### 2. Installer les dépendances
```bash
pip install -r requirements.txt
```

### 3. Configurer l'email
Dans `api_esg.py` ligne 69, remplace le mot de passe :
```python
EMAIL_MOT_DE_PASSE = "ton_mot_de_passe_app_gmail"
```
> Pour créer un mot de passe d'application Gmail : myaccount.google.com → Sécurité → Mots de passe des applications

### 4. Lancer l'API
```bash
python api_esg.py
```
L'API est disponible sur `http://localhost:5050`

### 5. Importer le workflow n8n
- Ouvrir n8n → Menu → **Import Workflow**
- Sélectionner `n8n_workflow_esg_v3.json`
- Configurer les credentials Gmail
- Activer le workflow ✅

---

## ☁️ Déploiement sur Render (optionnel)

Pour que le programme tourne 24h/24 sans ton PC :

1. Créer un compte sur [render.com](https://render.com)
2. New → Web Service → connecter ce repo GitHub
3. Start Command : `python api_esg.py`
4. Ajouter la variable d'environnement `EMAIL_MOT_DE_PASSE`
5. Dans n8n, remplacer `localhost:5050` par l'URL Render

---

## 📧 Contact
Développé par **InnovTech SA** — azizamara745@gmail.com
