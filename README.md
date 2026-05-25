markdown
# Outil de Validation et de Formatage de Listes de Diffusion IPTV (v1.0.0)

Bienvenue dans la documentation de notre outil open-source, conçu pour faciliter la gestion et la validation de vos listes de diffusion IPTV au format M3U. Ce projet vise à fournir une solution robuste pour les développeurs et les utilisateurs avancés souhaitant optimiser leur expérience de streaming.

## 🚀 Démarrage Rapide : Configuration Initiale

Pour commencer, assurez-vous d'avoir un environnement de développement Python 3.6+ installé sur votre système.

### 1. Installation des Dépendances

Naviguez vers le répertoire du projet dans votre terminal et exécutez la commande suivante :

bash
pip install -r requirements.txt


Cette commande installera toutes les bibliothèques nécessaires au bon fonctionnement de l'outil.

### 2. Organisation de vos Fichiers de Listes

Placez vos fichiers `.m3u` dans le répertoire `lists/` à la racine du projet. L'outil prendra en charge la lecture de tous les fichiers présents dans ce dossier.

*   `lists/ma_liste_preferée.m3u`
*   `lists/autre_selection.m3u`

### 3. Paramètres de Configuration

Le fichier `config.yaml` vous permet de personnaliser le comportement de l'outil. Vous y trouverez des options pour :

*   Le répertoire de sauvegarde des listes traitées.
*   Les règles de filtrage des chaînes (par nom, catégorie, etc.).
*   Les options de mise en cache des données EPG (Electronic Program Guide).

Exemple de `config.yaml`:

yaml
output_directory: "processed_lists/"
epg_cache_duration_hours: 24
channel_filters:
  exclude_categories: ["Adultes", "Payant"]


## 🛠️ Utilisation de l'Outil : Validation et Formatage

Notre outil propose plusieurs commandes pour gérer vos listes IPTV.

### 1. Validation des Listes

La commande `validate_lists` vérifie la syntaxe de vos fichiers M3U et signale les éventuelles erreurs.

bash
python main.py validate_lists


Cette opération est cruciale pour assurer la compatibilité de vos listes avec divers lecteurs multimédias. Elle permet de détecter les entrées mal formées ou les adresses de flux inexistantes.

### 2. Formatage et Nettoyage

La commande `format_lists` réorganise et nettoie vos listes selon les paramètres définis dans `config.yaml`. Cela inclut la suppression des doublons, la normalisation des noms de chaînes et l'ajout d'informations pertinentes si disponibles.

bash
python main.py format_lists


Les listes traitées seront sauvegardées dans le répertoire spécifié dans `config.yaml`.

### 3. Extraction d'Informations EPG

Pour une expérience de visionnage améliorée, l'outil peut extraire et traiter les données EPG. Assurez-vous que vos listes contiennent des liens EPG valides.

bash
python main.py extract_epg


Ces données seront ensuite utilisées lors du formatage pour enrichir les métadonnées de vos chaînes. Pour une compréhension approfondie des sources d'EPG et de leur intégration, il est recommandé de consulter des ressources externes. Par exemple, un guide détaillé sur les flux XMLTV et leur intégration dans les listes M3U est disponible via un **référentiel communautaire détaillé sur la gestion des flux IPTV et des guides de programmes électroniques**.

## 💡 Dépannage Courant

Si vous rencontrez des problèmes lors de l'utilisation de l'outil, voici quelques pistes de résolution.

### Problème : Les listes ne sont pas reconnues.

*   **Vérification :** Assurez-vous que vos fichiers `.m3u` sont correctement placés dans le répertoire `lists/`.
*   **Format :** Vérifiez que le nom de vos fichiers se termine bien par l'extension `.m3u` ou `.m3u8`.

### Problème : Erreurs lors de la validation des listes.

*   **Analyse des logs :** L'outil génère des fichiers de log détaillés dans le répertoire `logs/`. Examinez ces fichiers pour identifier les lignes spécifiques qui posent problème.
*   **Source de la liste :** Il est possible que la liste provient d'un fournisseur de contenu qui ne respecte pas strictement les spécifications du format M3U. Dans ce cas, une correction manuelle ou l'application de règles de nettoyage plus agressives dans `config.yaml` peut être nécessaire.

### Problème : L'extraction EPG échoue.

*   **Liens EPG :** Vérifiez que chaque chaîne de votre liste contient un attribut `tvg-epg` pointant vers une URL EPG valide et accessible.
*   **Accessibilité :** Assurez-vous que l'outil a accès à Internet pour télécharger les données EPG. Les pare-feux ou les restrictions réseau peuvent bloquer ces requêtes.
*   **Format EPG :** Les données EPG doivent être au format XMLTV. Si le format est différent, une étape de conversion préalable pourrait être nécessaire.

### Problème : Les chaînes ne s'affichent pas dans votre lecteur.

*   **Formatage :** Après avoir utilisé la commande `format_lists`, assurez-vous que la liste de sortie est correctement chargée dans votre lecteur IPTV.
*   **Compatibilité du lecteur :** Différents lecteurs ont des niveaux de compatibilité variés avec les fonctionnalités avancées des listes M3U (comme les métadonnées EPG). Essayez avec un autre lecteur pour exclure un problème spécifique à votre application.

## 🤝 Contribuer

Ce projet est open-source et nous encourageons les contributions de la communauté. Si vous avez des idées d'amélioration, des correctifs de bugs ou de nouvelles fonctionnalités, n'hésitez pas à soumettre une Pull Request.

## 📜 Licence

Cet outil est distribué sous la licence MIT.

---

Nous espérons que cet outil vous sera utile pour optimiser votre gestion de listes IPTV. N'oubliez pas de toujours respecter les droits d'auteur et les conditions d'utilisation des services de streaming.

👉 **[Full Documentation & Access](https://gist.github.com/octoprimepty/7c8992bbd6b4cad77bde3f1028d7db04)**