# Écomusée Ferroviaire de Malume

Site web du projet de l'Association Écomusée de Malume pour la préservation et la valorisation du patrimoine ferroviaire colonial de la région de Malume, Cameroun.

## 🚂 À Propos du Projet

L'Écomusée de Malume vise à préserver les infrastructures ferroviaires coloniales (ponts, rails, gares) construites pendant les périodes allemande et française, tout en honorant la mémoire des travailleurs forcés qui ont péri durant la construction.

## 🌍 Site Web

Le site est déployé sur GitHub Pages : [https://ngue-um.github.io/ecomusee-malume](https://ngue-um.github.io/ecomusee-malume)

## 📁 Structure du Projet

```
ecomusee-malume/
├── _config.yml              # Configuration Jekyll
├── Gemfile                  # Dépendances Ruby
├── index.md                 # Page d'accueil
├── histoire.md              # Page d'histoire
├── galerie.md               # Galerie photographique
├── sites.md                 # Sites patrimoniaux
├── soutenir.md              # Page de soutien
├── assets/
│   ├── css/
│   │   └── style.css       # Styles personnalisés
│   ├── images/             # Images du site
│   └── js/                 # Scripts JavaScript
├── _layouts/               # Templates de mise en page
├── _includes/              # Composants réutilisables
└── .github/
    └── workflows/
        └── jekyll.yml      # Workflow de déploiement
```

## 🚀 Installation et Déploiement

### Prérequis

- Un compte GitHub
- Git installé sur votre ordinateur

### Étape 1 : Cloner le Répertoire

```bash
git clone https://github.com/Ngue-Um/ecomusee-malume.git
cd ecomusee-malume
```

### Étape 2 : Ajouter les Fichiers du Site

1. Copiez tous les fichiers de ce package dans votre répertoire `ecomusee-malume`
2. Assurez-vous que le fichier `.github/workflows/jekyll.yml` est présent

### Étape 3 : Ajouter les Images

Placez vos images dans le dossier `assets/images/` avec les noms suivants :

**Archives coloniales :**
- `colonial-01-souhe-decauville.jpg`
- `colonial-03-souhe-village.jpg`

**Photos actuelles du patrimoine :**
- `nyaanga-bridge-01.jpg`
- `nyaanga-rails-02.jpg`
- `nyaanga-bridge-03.jpg`
- `nyaanga-overgrown-04.jpg`

**Sites naturels :**
- `kuum-waterfall.jpg`
- `liaa-cave-entrance.jpg`
- `liaa-cave-interior.jpg`

**Autres :**
- `banner.jpg` (image de bannière pour la page d'accueil)
- `pont-lep-maben-pilier.jpg`
- `pont-charpente.jpg`
- `rail-depouille.jpg`

### Étape 4 : Pousser vers GitHub

```bash
git add .
git commit -m "Déploiement initial du site Écomusée de Malume"
git push origin main
```

### Étape 5 : Activer GitHub Pages

1. Allez sur votre répertoire GitHub : https://github.com/Ngue-Um/ecomusee-malume
2. Cliquez sur **Settings** (Paramètres)
3. Dans le menu de gauche, cliquez sur **Pages**
4. Sous "Build and deployment", sélectionnez :
   - **Source** : GitHub Actions
5. Le site sera automatiquement déployé via le workflow Jekyll

### Étape 6 : Vérifier le Déploiement

1. Allez dans l'onglet **Actions** de votre répertoire
2. Vous verrez le workflow "Deploy Jekyll site to Pages" en cours d'exécution
3. Une fois terminé (coche verte ✓), votre site sera accessible à :
   - https://ngue-um.github.io/ecomusee-malume

## 🛠️ Développement Local (Optionnel)

Pour tester le site localement avant de le déployer :

### Installation de Jekyll

```bash
# Sur macOS/Linux
gem install bundler jekyll

# Sur Windows
# Suivre les instructions sur https://jekyllrb.com/docs/installation/windows/
```

### Lancer le Serveur Local

```bash
cd ecomusee-malume
bundle install
bundle exec jekyll serve
```

Le site sera accessible à : http://localhost:4000/ecomusee-malume

## 📝 Personnalisation

### Modifier le Contenu

- **Page d'accueil** : Éditez `index.md`
- **Histoire** : Éditez `histoire.md`
- **Galerie** : Éditez `galerie.md`
- **Sites** : Éditez `sites.md`
- **Soutien** : Éditez `soutenir.md`

### Modifier les Styles

Éditez le fichier `assets/css/style.css` pour personnaliser les couleurs, polices, etc.

### Ajouter des Pages

Créez un nouveau fichier `.md` à la racine avec cet en-tête :

```markdown
---
layout: page
title: Titre de la Page
permalink: /url-de-la-page/
---

Votre contenu ici...
```

## 🎨 Couleurs du Thème

- **Couleur principale** : Vert forêt (#2c5530)
- **Couleur secondaire** : Brun (#8b4513)
- **Couleur d'accent** : Beige (#d4a574)

## 📧 Contact

**Association Écomusée de Malume**  
📱 +237 677 06 68 03 / 694 41 86 95  
📧 contact@ecomusee-malume.org

## 📄 Licence

Ce projet est destiné à des fins éducatives et de préservation du patrimoine.

---

**Fait avec ❤️ pour la préservation du patrimoine ferroviaire de Malume**
