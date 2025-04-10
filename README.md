# AutoMakefile

Un générateur automatique de Makefile pour les projets en C, conçu pour simplifier la configuration et la compilation des projets.

## Description

AutoMakefile est un script bash qui génère automatiquement un Makefile personnalisé à partir d'un fichier de configuration. Il est particulièrement utile pour les projets EPITECH et autres projets en C qui nécessitent une structure de compilation standardisée.

## Fonctionnalités

- Génération automatique de Makefile à partir d'un fichier de configuration
- Prise en charge des répertoires sources, headers et bibliothèques 
- Configuration personnalisée du compilateur et des flags
- Système intégré de sauvegarde et de restauration (archive)
- Gestion des versions de sauvegarde (création, restauration, suppression)

## Installation

Clonez le dépôt et rendez le script exécutable :

```bash
git clone git@github.com:Amayyas/AutoMakefile.git
cd AutoMakefile
chmod +x automakefile
```

## Utilisation

1. Créez un fichier de configuration (par exemple, `config.txt`) avec la structure suivante :

```
PROJECT_DIR;/chemin/vers/votre/projet
SOURCES_DIR;src
HEADERS_DIR;include
LIBS_DIR;lib
EXEC;nom_executable
CC;gcc
CFLAGS;-Wall -Wextra -Werror
LDFLAGS;-lm
fichier1.c;description
fichier2.c;description
```

2. Exécutez le script avec le fichier de configuration en argument :

```bash
./automakefile config.txt
```

3. Un Makefile sera généré dans le répertoire spécifié.

## Configuration

Le fichier de configuration utilise le format `clé;valeur` :

- `PROJECT_DIR` : Chemin vers le répertoire du projet (obligatoire)
- `SOURCES_DIR` : Répertoire des fichiers sources
- `HEADERS_DIR` : Répertoire des fichiers d'en-tête
- `LIBS_DIR` : Répertoire des bibliothèques
- `EXEC` : Nom de l'exécutable
- `CC` : Compilateur à utiliser
- `CFLAGS` : Flags de compilation
- `LDFLAGS` : Flags de liaison
- `BCK_DIR` : Répertoire de sauvegarde (par défaut: "backup")
- `ZIP`, `ZIPFLAGS`, `UNZIP`, `UNZIPFLAGS` : Configuration des outils d'archivage

Tous les autres champs sont considérés comme des fichiers sources.

## Commandes du Makefile généré

Le Makefile généré inclut les règles standard :

- `make` ou `make all` : Compile le projet
- `make clean` : Supprime les fichiers objets
- `make fclean` : Supprime les fichiers objets et l'exécutable
- `make re` : Effectue `fclean` puis `all`

Et des commandes supplémentaires de gestion d'archives :

- `make archive` : Crée une archive du projet
- `make revert` : Restaure la dernière archive
- `make num` : Affiche le numéro de la dernière archive
- `make delete` : Supprime la dernière archive
