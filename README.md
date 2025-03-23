# Curriculum Vitae | Baptiste ROY

Ce dépôt contient le code source de mon CV, généré dynamiquement à partir de fichiers AsciiDoc et déployé automatiquement sur GitHub Pages.

## 📄 À propos

Mon CV est écrit en format AsciiDoc, qui permet de générer une page statique responsive ainsi qu'une maintenance facile. Il est ensuite converti en HTML à l'aide des outils AsciiDoctor, puis déployé automatiquement sur GitHub Pages.

🔗 **Voir mon CV en ligne**: [https://roybaptiste.github.io/cv/](https://roybaptiste.github.io/cv/)

## 🛠️ Architecture technique

- **Source**: Fichiers AsciiDoc (principalement `src/index.adoc`)
- **Style**: CSS personnalisé dans `src/css/custom.css`
- **Construction**: Via Docker et AsciiDoctor
- **Déploiement**: GitHub Actions vers GitHub Pages

## 🚀 Processus de déploiement automatisé
'
Le déploiement est entièrement automatisé grâce à GitHub Actions:

1. À chaque push sur la branche `main` associé au `src/**` & `cv-gh_pages.yml`(ou déclenchement manuel)
2. Le conteneur Docker génèrent le fichier HTML
3. Le fichier généré est déployé dans le dépôt GitHub Pages

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

## 📜 Licence

Ce projet est sous licence [MIT](https://opensource.org/licenses/MIT).