# Guide de Déploiement - Écomusée de Malume

Ce guide vous explique pas à pas comment déployer votre site web sur GitHub Pages.

## 📋 Ce Dont Vous Avez Besoin

1. ✅ Un compte GitHub (vous l'avez déjà)
2. ✅ Le répertoire `ecomusee-malume` sur GitHub (vous l'avez déjà)
3. ✅ Les fichiers du site (fournis dans ce package)
4. ✅ Git installé sur votre ordinateur ([Télécharger Git](https://git-scm.com/downloads))

## 🚀 Étapes de Déploiement

### Étape 1 : Télécharger le Package

Vous avez déjà reçu le dossier `ecomusee-site` contenant tous les fichiers nécessaires.

### Étape 2 : Cloner Votre Répertoire GitHub

Ouvrez un terminal (ou Git Bash sur Windows) et tapez :

```bash
cd ~/Desktop  # ou tout autre dossier où vous voulez travailler
git clone https://github.com/Ngue-Um/ecomusee-malume.git
cd ecomusee-malume
```

### Étape 3 : Vérifier le Workflow Jekyll

Vérifiez que le fichier `.github/workflows/jekyll.yml` existe dans votre répertoire. Si ce n'est pas le cas, créez-le avec ce contenu :

```yaml
name: Deploy Jekyll site to Pages
on:
  push:
    branches: ["main"]
  workflow_dispatch:
permissions:
  contents: read
  pages: write
  id-token: write
concurrency:
  group: "pages"
  cancel-in-progress: false
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Setup Ruby
        uses: ruby/setup-ruby@v1
        with:
          ruby-version: "3.3"
          bundler-cache: true
      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v5
      - name: Build with Jekyll
        run: bundle exec jekyll build --baseurl "${{ steps.pages.outputs.base_path }}"
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: "_site"
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

### Étape 4 : Copier les Fichiers du Site

Copiez TOUS les fichiers du dossier `ecomusee-site` dans votre répertoire `ecomusee-malume` :

```bash
# Sur Mac/Linux
cp -r ~/chemin/vers/ecomusee-site/* ~/Desktop/ecomusee-malume/

# Sur Windows (dans l'explorateur de fichiers)
# Copiez manuellement tous les fichiers
```

Votre structure devrait ressembler à ceci :

```
ecomusee-malume/
├── .github/
│   └── workflows/
│       └── jekyll.yml
├── .gitignore
├── _config.yml
├── Gemfile
├── README.md
├── index.md
├── histoire.md
├── galerie.md
├── sites.md
├── soutenir.md
├── a-propos.md
└── assets/
    ├── css/
    │   └── style.css
    └── images/
        ├── colonial-01-souhe-decauville.jpg
        ├── colonial-03-souhe-village.jpg
        ├── nyaanga-bridge-01.jpg
        ├── nyaanga-rails-02.jpg
        ├── nyaanga-bridge-03.jpg
        └── nyaanga-overgrown-04.jpg
```

### Étape 5 : Ajouter une Image de Bannière

Créez ou choisissez une image de bannière (1200x400 pixels recommandé) et nommez-la `banner.jpg`. Placez-la dans `assets/images/`.

### Étape 6 : Pousser vers GitHub

Dans votre terminal :

```bash
cd ~/Desktop/ecomusee-malume
git add .
git commit -m "Déploiement initial du site Écomusée de Malume"
git push origin main
```

Si c'est la première fois que vous utilisez Git, vous devrez peut-être configurer votre identité :

```bash
git config --global user.email "votre.email@example.com"
git config --global user.name "Votre Nom"
```

### Étape 7 : Activer GitHub Pages

1. Allez sur https://github.com/Ngue-Um/ecomusee-malume
2. Cliquez sur **Settings** (⚙️ en haut à droite)
3. Dans le menu de gauche, descendez et cliquez sur **Pages**
4. Sous "Build and deployment" :
   - **Source** : Sélectionnez "GitHub Actions"
5. La configuration est terminée !

### Étape 8 : Vérifier le Déploiement

1. Allez dans l'onglet **Actions** en haut de votre répertoire
2. Vous verrez un workflow en cours d'exécution : "Deploy Jekyll site to Pages"
3. Attendez que le workflow se termine (coche verte ✅)
4. Cliquez sur le workflow pour voir les détails

### Étape 9 : Accéder à Votre Site

Une fois le déploiement terminé, votre site sera accessible à :

🌐 **https://ngue-um.github.io/ecomusee-malume**

⏱️ Le premier déploiement peut prendre 2-5 minutes.

## 🔄 Mettre à Jour le Site

Pour modifier le contenu du site à l'avenir :

1. Modifiez les fichiers localement
2. Testez les changements (optionnel, voir section suivante)
3. Poussez vers GitHub :

```bash
git add .
git commit -m "Description de vos changements"
git push origin main
```

Le site se mettra à jour automatiquement !

## 🧪 Tester Localement (Optionnel)

Pour voir vos changements avant de les déployer :

### Installation de Jekyll

**Sur Mac :**
```bash
gem install bundler jekyll
```

**Sur Windows :**
Suivez le guide : https://jekyllrb.com/docs/installation/windows/

**Sur Linux :**
```bash
sudo apt-get install ruby-full build-essential
gem install bundler jekyll
```

### Lancer le Serveur Local

```bash
cd ~/Desktop/ecomusee-malume
bundle install
bundle exec jekyll serve
```

Ouvrez votre navigateur à : http://localhost:4000/ecomusee-malume

## ❓ Résolution des Problèmes

### Le workflow échoue avec une erreur Ruby

Vérifiez que votre `Gemfile` est correct et que les versions Ruby correspondent.

### Le site ne se charge pas

1. Vérifiez que le workflow s'est exécuté avec succès
2. Attendez quelques minutes de plus
3. Videz le cache de votre navigateur (Ctrl+Shift+R ou Cmd+Shift+R)

### Les images ne s'affichent pas

Vérifiez que :
1. Les images sont bien dans `assets/images/`
2. Les noms de fichiers correspondent exactement à ceux référencés dans les pages
3. Les chemins utilisent `/ecomusee-malume/assets/images/...`

### GitHub Actions n'est pas disponible

Assurez-vous que GitHub Actions est activé :
1. Settings → Actions → General
2. "Allow all actions and reusable workflows" doit être sélectionné

## 📝 Modifications Courantes

### Changer le Titre du Site

Éditez `_config.yml` :
```yaml
title: Nouveau Titre
```

### Ajouter une Page

Créez un fichier `nouvelle-page.md` :
```markdown
---
layout: page
title: Titre de la Page
permalink: /nouvelle-page/
---

Contenu ici...
```

### Modifier les Couleurs

Éditez `assets/css/style.css` et modifiez les valeurs dans `:root`.

## 📞 Besoin d'Aide ?

Si vous rencontrez des difficultés :
1. Consultez la documentation Jekyll : https://jekyllrb.com/docs/
2. Vérifiez les issues GitHub : https://github.com/jekyll/jekyll/issues
3. Contactez un développeur familier avec Jekyll

## ✅ Checklist Finale

Avant de considérer le déploiement comme terminé :

- [ ] Tous les fichiers sont copiés dans le répertoire
- [ ] Le workflow Jekyll est configuré
- [ ] Les images sont dans `assets/images/`
- [ ] GitHub Pages est activé avec "GitHub Actions"
- [ ] Le workflow s'est exécuté avec succès
- [ ] Le site est accessible à l'URL
- [ ] Toutes les pages se chargent correctement
- [ ] Les images s'affichent
- [ ] Les liens de navigation fonctionnent

## 🎉 Félicitations !

Votre site est maintenant en ligne et contribue à la préservation du patrimoine de Malume !

---

**Questions ? Contactez :**
📱 +237 677 06 68 03 / 694 41 86 95
