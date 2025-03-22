# Curriculum Vitae | Baptiste ROY

Ce dépôt contient le code source de mon CV, généré dynamiquement à partir de fichiers AsciiDoc et déployé automatiquement sur GitHub Pages.

## 📄 À propos

Mon CV est écrit en format AsciiDoc, qui permet une mise en forme riche et une maintenance facile. Il est ensuite converti en HTML et PDF à l'aide des outils AsciiDoctor, puis déployé automatiquement sur GitHub Pages.

🔗 **Voir mon CV en ligne**: [https://roybaptiste.github.io/cv/](https://roybaptiste.github.io/cv/)

## 🛠️ Architecture technique

- **Source**: Fichiers AsciiDoc (principalement `src/index.adoc`)
- **Style**: CSS personnalisé dans `src/css/custom.css`
- **Construction**: Via Docker et AsciiDoctor
- **Déploiement**: GitHub Actions vers GitHub Pages

## 🔍 Caractéristiques du design

Le CV a été conçu avec une attention particulière aux détails :

- **Design responsive** : S'adapte aux différentes tailles d'écran
- **Interface moderne** : Utilisation d'une palette de couleurs professionnelle
- **Structure claire** : Organisation chronologique des expériences
- **Mise en valeur des compétences** : Utilisation de tags pour identifier rapidement les technologies
- **Sections bien définies** : Profil personnel, expériences professionnelles, compétences et centres d'intérêt

## 🚀 Processus de déploiement automatisé

Le déploiement est entièrement automatisé grâce à GitHub Actions:

1. À chaque push sur la branche `main` (ou déclenchement manuel)
2. Les conteneurs Docker génèrent les fichiers HTML et PDF
3. Les fichiers générés sont déployés dans le dépôt GitHub Pages

### Configuration du déploiement

Le workflow de déploiement est défini dans `.github/workflows/cv-gh_pages.yml`. Il utilise:

- L'image Docker `asciidoctor/docker-asciidoctor` pour la génération des documents
- L'action GitHub `tonynv/asciidoctor-action` pour la génération HTML
- Une clé SSH pour l'authentification au dépôt GitHub Pages

## 💻 Développement local

### Prérequis

- Docker
- Docker Compose

### Génération locale du CV

```bash
# Créer le dossier de sortie
mkdir -p dist

# Définir les variables d'environnement
export CURRENT_UID=$(id -u):$(id -g)
export CV_URL="https://roybaptiste.github.io/cv"
export SOURCE_URL="https://github.com/roybaptiste/AsciiDoctorGenerator"
export SHORT_OWNER_NAME="roy-baptiste"

# Générer le HTML et le PDF
docker-compose up html pdf
```

## 📝 Modification du CV

Pour mettre à jour le CV:

1. Modifiez les fichiers dans le dossier `src/`, principalement `src/index.adoc`
2. Personnalisez le style dans `src/css/custom.css`
3. Commitez et poussez les modifications
4. Le workflow GitHub Actions se déclenchera automatiquement
5. Vérifiez le résultat sur [https://roybaptiste.github.io/cv/](https://roybaptiste.github.io/cv/)

> **Note:** Le fichier `src/index.adoc` contient une référence à `:imagesdir: ./images/` qui sera utilisée si vous ajoutez des images à votre CV.

### Suppression de fichiers

Si vous souhaitez supprimer des fichiers du CV déployé:

1. Supprimez le fichier correspondant dans le dossier `src/`
2. Commitez la suppression avec `git rm [nom-du-fichier]`
3. Poussez les modifications
4. GitHub Actions mettra à jour le site déployé en conséquence

## 📊 Structure du projet

```
AsciiDoctorGenerator/
├── .github/
│   └── workflows/
│       └── cv-gh_pages.yml    # Workflow GitHub Actions
├── src/
│   ├── css/
│   │   └── custom.css         # Styles personnalisés
│   └── index.adoc             # Contenu principal du CV
├── dist/                      # Fichiers générés (local)
├── docker-compose.yml         # Configuration Docker pour génération locale
└── README.md                  # Documentation
```

## 🔧 Personnalisation

Le CV peut être facilement personnalisé :

- Modifiez `src/index.adoc` pour changer le contenu et la structure
- Ajustez `src/css/custom.css` pour personnaliser l'apparence
- Utilisez les attributs AsciiDoc pour configurer le document
- Pour ajouter des images, créez un dossier `src/images/` au besoin

## 📜 Licence

Ce projet est sous licence open source - voir le fichier [LICENSE](LICENSE) pour plus de détails. 