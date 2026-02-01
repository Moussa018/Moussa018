# 👋 Salut, moi c'est [Ton Nom] !

### 🚀 En plein apprentissage de Rust
*Actuellement, je travaille sur un convertisseur CSV vers Parquet pour comparer les performances avec Python.*

---

## 📊 Mes Statistiques GitHub
![Stats de [Ton Nom]](https://github-readme-stats.vercel.app/api?username=TON_PSEUDO&show_icons=true&theme=radical)

## 🛠 Langages et Outils
![Rust](https://img.shields.io/badge/rust-%23E32F26.svg?style=for-the-badge&logo=rust&logoColor=white)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)

---

## 🔄 Activité Dynamique
Last updated: ```

---

## 2. Comment la rendre "Dynamique" ?
Pour que ta bio change toute seule (par exemple pour afficher l'heure, la météo ou tes derniers commits), voici comment faire :

### Étape A : Créer le script de mise à jour
Dans ton dépôt, crée un dossier `.github/workflows/` et à l'intérieur, un fichier nommé `update_bio.yml`.

### Étape B : Ajouter le code magique
Copie ce code dans le fichier `.github/workflows/update_bio.yml`. Ce script va écrire la date du jour automatiquement dans ton README toutes les 24 heures.

```yaml
name: Update README

on:
  schedule:
    - cron: '0 0 * * *' # S'exécute tous les jours à minuit
  workflow_dispatch: # Permet de le lancer manuellement

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Update date
        run: |
          DATE=$(date +'%Y-%m-%d %H:%M:%S')
          sed -i "s//$DATE/" README.md
      - name: Commit changes
        run: |
          git config --local user.email "action@github.com"
          git config --local user.name "GitHub Action"
          git add README.md
          git commit -m "Update dynamic content" || exit 0
          git push
