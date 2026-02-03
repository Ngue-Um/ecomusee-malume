# Écomusée Ferroviaire de Malume

Site web officiel de l'Association Écomusée de Malume pour la préservation et la valorisation du patrimoine ferroviaire colonial de la région de Malume, Cameroun.

## 🚀 Déploiement Rapide

### Étape 1 : Nettoyer le Répertoire GitHub

Votre répertoire contient actuellement des fichiers anciens. **Important : Vous devez supprimer TOUS les fichiers existants avant d'ajouter les nouveaux.**

```bash
# Cloner le répertoire
git clone https://github.com/Ngue-Um/ecomusee-malume.git
cd ecomusee-malume

# Supprimer TOUS les fichiers existants (sauf .git)
find . -not -path "./.git/*" -not -name ".git" -delete

# Copier TOUS les nouveaux fichiers depuis ce package
cp -r /chemin/vers/nouveaux/fichiers/* .

# Vérifier que vous avez bien :
ls -la
# Vous devriez voir : _config.yml, _layouts/, assets/, index.md, etc.
```

### Étape 2 : Pousser vers GitHub

```bash
git add .
git commit -m "Refonte complète du site - Version propre"
git push origin main --force
```

**Note :** Le `--force` est nécessaire car nous remplaçons complètement l'historique.

### Étape 3 : Vérifier le Déploiement

1. Allez sur https://github.com/Ngue-Um/ecomusee-malume/actions
2. Attendez que le workflow se termine (coche verte ✓)
3. Visitez https://ngue-um.github.io/ecomusee-malume

## 📁 Structure du Site

```
ecomusee-malume/
├── _config.yml              # Configuration du site
├── Gemfile                  # Dépendances Ruby
├── index.md                 # Page d'accueil
├── histoire.md              # Histoire du chemin de fer
├── galerie.md               # Galerie photos
├── sites.md                 # Sites patrimoniaux
├── a-propos.md              # À propos
├── soutenir.md              # Comment soutenir
├── _layouts/
│   ├── default.html         # Layout principal
│   └── page.html            # Layout des pages
├── assets/
│   ├── css/
│   │   └── main.css         # Styles personnalisés
│   └── images/              # Images du site
└── .github/
    └── workflows/
        └── jekyll.yml       # Déploiement automatique
```

## 🎨 Personnalisation

### Modifier le Contenu

Éditez les fichiers `.md` avec un éditeur de texte.

### Changer les Couleurs

Modifiez `assets/css/main.css`, section `:root` :

```css
:root {
  --primary-color: #2c5530;   /* Vert principal */
  --secondary-color: #6b8e23;  /* Vert secondaire */
  --accent-color: #d4a574;     /* Accent beige */
}
```

### Ajouter une Page

Créez un fichier `nouvelle-page.md` :

```markdown
---
layout: page
title: Titre de la Page
---

Contenu...
```

## 📧 Contact

**Association Écomusée de Malume**  
📱 +237 677 06 68 03 / 694 41 86 95  
📧 contact@ecomusee-malume.org

## ⚠️ Important

Ce nouveau site est **propre et moderne**. Il n'y a plus de :
- Pages de documentation (INSTALLATION.md, DEPLOIEMENT.md, etc.)
- Dossiers imbriqués (ecomusee-site/)
- Thème de documentation ("Just the Docs")

Le site utilise maintenant un design simple, moderne et responsive similaire à l'exemple que vous avez fourni.
