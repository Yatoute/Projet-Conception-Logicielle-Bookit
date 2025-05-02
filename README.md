# Bookit - Application de réservation de services


## 🎓 Contexte

Ce projet a été réalisé dans le cadre du cours de **Conception de logiciel** en **2ᵉ année** à l'**ENSAI**. Il vise à appliquer les principes d'ingénierie de développement afin de concevoir une application complète et fonctionnelle répondant à un besoin concret.


## 📖 Description

**Bookit** est une application de réservation des services tels que des **bus**, **salles** et **matériaux**. Elle permet de centraliser la gestion des ressources, de visualiser les disponibilités des ressources, et de permettre aux utilisateurs de faire des réservations facilement.


### ✨ Fonctionnalités principales

1. **s'inscrire, se connecter, se déconnecter, se désinscrire**
   
3. **Gestion des utilisateurs**:
   
   Nous avons 3 types d'utilisateurs:
   - [ ]  *Consumer*: Utilisateur classique, peut consulter les évenements, réserver des ressources et gérer ses réservations
   - [ ]  *Event Admin*: Administrateur d'événements, peut créer, modifier, supprimer et gérer des événements (bus, salles, matériel)
   - [ ]  *Admin*: Administrateur principal, avec des droits étendus pour gérer les utilisateurs, ressources et les configurations générales de l'application

3. **Création et gestion des événements**:
   - [ ] Création des événements pour la réservation de bus, salles ou matériel.
   - [ ] Mise  à jour ou supprimer des événements existants.
   - [ ] Liste des événements disponibles

3. **Réservation des ressources**
   - [ ] *Bus* : Réservation de places pour des événements spécifiques (par exemple, transport pour des sorties).
   - [ ] *Salles* : Réservation de salles pour des événements comme des conférences, cours, ou activités.
   - [ ] *Matériel* : Réservation de matériel pour des événements particuliers.
   - [ ] Les utilisateurs peuvent également annuler leurs réservations si nécessaire

7. **Notifications automatiques**
   
      Lorsqu'un événement est créé ou mis à jour, une notification par e-mail est envoyée à tous les consommateurs inscrits pour les tenir informés des nouvelles disponibilités et modifications des événements.

   

## 💻 Technologies utilisées
- [ ] Backend: Django
- [ ] Frontend: React
- [ ] Base de données: SQLite
- [ ] Conteneurisation et déploiement : Docker, Kubernetes
- [ ] CI/CD : GitHub Actions


## 🚀 Quickstart (Démarrage rapide)

### :arrow_forward: Application délpoyée

L'application est déployée avec sur Kubernetes et accessible à l'adresse suivante: [https://bookit-ensai.kub.sspcloud.fr/](https://bookit-ensai.kub.sspcloud.fr/)

### :arrow_forward: Lancer l'application via Docker Hub

Assurez-vous d'avoir installé Docker (ou Docker Desktop sous windows) sur votre machine.
Vous allez lancer l'application en utilisant les images docker que nous avons publié sur Docker Hub


- [ ] Cloner le projet:
      
   Récupérez le code source en clonant ce dépôt sur votre machine locale :
```bash
git clone https://github.com/Yatoute/Projet-Conception-Logicielle-Bookit.git
cd Projet-Conception-Logicielle-Bookit
```

- [ ] Configurer les variables d'environnements:
      
   Avant de lancer l'application, vous devez définir certaines variables d'environnement nécessaires au bon fonctionnement de l'application:
      
1. Copiez le fichier `.env.template` et renommez-le en `.env` :

   Exécutez les commandes suivantes pour dupliquer le fichier modèle .env.template et créer le fichier .env qui sera utilisé par votre application :
```bash
cp backend/.env.template backend/.env
cp frontend/.env.template frontend/.env
```

2. Complétez les variables d'environnement dans le fichier `.env`  du backend :

   Ouvrez le fichier .env du backend et remplissez les variables avec les valeurs appropriées. Certaines variables sont déjà renseignées par défaut(vous pouvez ajuster ces valeurs selon vos besoins)

   Voici les variables à compléter :

- **DJANGO_SUPERUSER_USERNAME** : Entrez un nom d'utilisateur pour l'administrateur Django.
- **DJANGO_SUPERUSER_EMAIL** : Entrez l'email de l'administrateur Django.
- **DJANGO_SUPERUSER_PASSWORD** : Entrez un mot de passe pour l'administrateur Django.
- **DJANGO_SECRET_KEY** : Générez une nouvelle clé secrète Django. Vous pouvez utiliser la commande suivante pour générer une clé secrète:
  ```bash
  python -c 'from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())'
  ```
- **DJANGO_DEBUG** : Valeur par défaut True. Changez-la en False pour un environnement de production.
- **DJANGO_ALLOWED_HOSTS** : Liste des hôtes autorisés. La valeur par défaut inclut localhost et 127.0.0.1, mais Vous devrez l'ajuster si votre application doit être accessible depuis d'autres hôtes.
- **FRONTEND_APP_API_URL** : Liste des URL de l'API frontend. La valeur par défaut inclut http://localhost:3000, https://bookit-ensai.kub.sspcloud.fr
- **EMAIL_HOST_USER** et **EMAIL_HOST_PASSWORD** : Entrez les informations de connexion de votre serveur SMTP pour l'envoi d'emails. Ces champs sont vides par défaut. Si vous utilisez Gmail, remplissez-les avec les informations nécessaires pour l'authentification via le service Gmail. Assurez-vous de bien sécuriser ces informations.


- [ ] Pull des images depuis Docker Hub

```bash
docker pull yatoute/bookit-backend:latest
docker pull yatoute/bookit-frontend:latest
```

- [ ] Exécuter l'application
  - backend
  ```bash
  docker run --env-file backend/.env -p 8000:8000 yatoute/bookit-backend:latest
  ```

  - frontend
  ```bash
  docker run -d -e NEXT_PUBLIC_API_URL=http://127.0.0.1:8000 -p 3000:3000 --name bookit-frontend yatoute/bookit-frontend:latest
  ```
  
- [ ] Accéder à l'application :

Une fois les services démarrés, accédez au :

Backend :  [http://127.0.0.1:8000](http://127.0.0.1:8000)
Frontend : [http://localhost:3000](http://localhost:3000)


## 📌 Instructions pour lancer l'application en local

Assurez-vous d'avoir **Node.js** installé sur votre machine(pour le frontend).
Vous pouvez installer Node.js via nvm, le gestionnaire de version de Node.js:

- [ ] Installation de nvm (Node Version Manager)
      
   Si nvm n'est pas déjà installé sur votre système, suivez les étapes ci-dessous pour l'installer

   1. Installer nvm
   
   Exécutez la commande suivante dans votre terminal pour installer nvm :
   ```bash
   curl -fsSL https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.4/install.sh | bash
   ```
   2. Appliquer les modifications au shell
   
   Après l'installation de nvm, rechargez votre shell pour appliquer les changements :
   ```bash
   source ~/.bashrc
   ```
   3. Vérifier l'installation de nvm
   
   Vérifiez que nvm est correctement installé en exécutant :
   ```bash
   nvm --version
   ```
   Si la version de nvm est affichée, l'installation a réussi.

- [ ] Installer Node.js 20

Une fois nvm installé, vous pouvez utiliser nvm pour installer la version de Node.js 20, qui est requise pour le projet. Exécutez les commandes suivantes :

   1. Installer Node.js 20 :
   ```bash
   nvm install 20
   ```

   2. Définir Node.js 20 comme version par défaut :
   ```bash
   nvm use 20
   nvm alias default 20
   ```

   3. Vérifier l'installation de Node.js et npm
   
   Pour confirmer que Node.js et npm sont installés correctement, exécutez les commandes suivantes :
   ```bash
   node -v
   npm -v
   ```
   Cela affichera les versions respectives de Node.js et npm.
   

- [ ] Créez un environnement virtuel :
  ```bash
  python -m venv venv
  ```
  - Sur Mac/Linux
  ```bash
  source venv/bin/activate
  ```
  - Sur windows
     ```bash
     source venv/bin/activate
     ```

 - [ ] Installer les dépendances
   - Backend
  ```bash
  pip install -r backend/requirements.txt
  ```
   - Frontend
  ```bash
  cd frontend
  npm install
  ```

- [ ] Appliquer les migrations :
```bash
cd ../backend
python manage.py makemigrations
python manage.py migrate
```

- [ ] Initialisation de données dans la base:
      
Vous pouvez **initialiser des données** dans la base en lançant le srcipt d'initiliasation des données initlize_data.py contenu dans le dossier backend/backend/management/commands/
Pour faire cela, exécutez la commande:

```bash
python manage.py initialize_data
```

- [ ] Lancer le backend :
      
```bash
python manage.py runserver
```
L'application backend sera accessible à [http://127.0.0.1:8000](http://127.0.0.1:8000)

- [ ] Lancer le frontend :
```bash
cd frontend
npm run dev
```
L'application frontend sera accessible à [http://localhost:3000](http://localhost:3000)


## 📈 Tests unitaires
Les tests unitaires sont automatisés à chaque push via GitHub Actions.
Pour lancer les tests manuellement, exécutez:
```bash
cd backend
coverage run manage.py test
coverage html
```
Ensuite vous pouvez ouvrir le fichier `coverage_report/index.html` dans votre navigateur pour consulter le rapport de couverture des tests.


## 🛠️ Automatisation

Le projet utilise GitHub Actions pour automatiser les tests, la vérification du code à chaque push et le déploiement des images Docker vers Docker Hub


## 🎯 Scénario d'utilisation de l'application

Imaginons un utilisateur souhaitant réserver une salle: 

1. **Création du compte utilisateur** :

   L'utilisateur se rend sur la page d'inscription de l'application. Il s'inscrit donc en tant que "Consumer" avec nom d(utilisateur s, on adresse e-mail et un mot de passe.

2. **Connexion** :

   L'utilisateur se connecte avec ses identifiants (Nom d'utilisateur et mot de passe) via la page de connexion. Après la connexion, l'utilisateur accède à son tableau de bord, où il peut consulter les événements disponibles (salles, bus, matériel).
   

3. **Réservation d'une salle** :

   L'utilisateur sélectionne une salle disponible et réserve la date et l'heure qui lui convient. Il peut alors voir  la réservation apparaître dans son tableau de bord.

4. **Annulation d'une réservation** :

   Si l'utilisateur décide de ne plus utiliser la salle, il peut annuler sa réservation via son tableau de bord.

5. **Déconnexion** :
   
   L'utilisateur se déconnecte de l'application avec le bouton de déconnexion


## 👥 Équipe du projet
Le projet est réalisé par les élèves:
- [ ] **Richard GOZAN**
- [ ] **Alex LABOU**
- [ ] **Yatoute MINTOMA**

Sous la supervision de :
- [ ] **M. Antoine Brunetti**: Analyste Développeur à l'INSEE
- [ ] **Mme Oriane Foussard**: Analyste Développeur à l'INSEE
