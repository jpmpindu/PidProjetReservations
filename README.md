# 📘 Projet Reservations – Documentation Complète

## 🐳 1. Installation de Docker
Avant de lancer ce projet, vous devez installer Docker sur votre système. Voici les étapes pour **Windows**, **Linux** et **macOS**.

---

## 🪟 1.1 Installer Docker sur Windows
### Prérequis :
- Windows 10/11 Pro, Enterprise ou Education
- Hyper‑V activé

### Étapes :
1. Téléchargez Docker Desktop pour Windows depuis le site officiel.
2. Installez-le et suivez les instructions.
3. Redémarrez votre ordinateur.
4. Lancez Docker Desktop.

### Démarrer Docker sur Windows :
Docker Desktop se lance automatiquement. Sinon :
```
Menu Démarrer → Docker Desktop
```
Attendez que le message **Docker is running** apparaisse.

---

## 🐧 1.2 Installer Docker sur Linux
L’installation dépend de votre distribution. Exemple pour Ubuntu :

### Étapes :
```bash
sudo apt update
sudo apt install ca-certificates curl gnupg
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker.gpg
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io
```

### Démarrer Docker sur Linux :
```bash
sudo systemctl start docker
sudo systemctl enable docker
```

---

## 🍎 1.3 Installer Docker sur macOS
### Étapes :
1. Téléchargez Docker Desktop pour macOS depuis le site officiel.
2. Glissez Docker.app dans **Applications**.
3. Lancez Docker.
4. Autorisez les permissions nécessaires.

### Démarrer Docker sur macOS :
Docker se lance automatiquement. Sinon :
```
Applications → Docker
```
Attendez le message **Docker is running**.

---

# 🧬 2. Cloner le Projet
Exécutez la commande suivante :
```bash
git clone https://github.com/jpmpindu/PidProjetReservations.git
cd PidProjetReservations
cd reservations
```

Vous verrez maintenant cette structure de fichiers.

---

# 🗂️ 3. Architecture du Projet
```
reservations/
│
├── .gitignore
├── README.md
├── docker-compose.yml
├── Dockerfile
├── manage.py
├── .env.example
│
├── accounts/
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── tests.py
│   ├── urls.py
│   ├── views.py
│   ├── forms/
│   ├── migrations/
│   └── templates/
│
├── catalogue/
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── tests.py
│   ├── urls.py
│   ├── views.py
│   ├── fixtures/
│   ├── forms/
│   ├── migrations/
│   ├── models/
│   └── templates/
│
└── reservations/
    ├── __init__.py
    ├── asgi.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py
```

---

# 📝 4. Explication des Fichiers et Dossiers

## Fichiers à la racine
### **.gitignore**
Définit les fichiers à ignorer par Git.

### **README.md**
Documentation du projet.

### **docker-compose.yml**
Définit les services (Django, MySQL, etc.) et leur configuration.

### **Dockerfile**
Construit l’image Docker de l’application Django.

### **manage.py**
Outil en ligne de commande de Django pour lancer le serveur, effectuer les migrations, etc.

### **.env.example**
Template contenant les variables d’environnement nécessaires. Dupliquez-le :
```bash
cp .env.example .env
```

---

## L’App "accounts"
Gère la gestion des utilisateurs.

### Fichiers :
- **__init__.py** → Initialise le package Python
- **admin.py** → Configuration de l’admin
- **apps.py** → Configuration de l’app Django
- **models.py** → Modèles de base de données
- **tests.py** → Tests unitaires
- **urls.py** → Routes de l’app
- **views.py** → Logique pour les réponses HTTP

### Dossiers :
- **forms/** → Formulaires Django (inscription, connexion…)
- **migrations/** → Fichiers de migration automatiques
- **templates/** → Templates HTML

---

## L’App "catalogue"
Gère les produits, menus et données du catalogue.

### Fichiers :
Même structure que `accounts`, plus :
- **fixtures/** → Données initiales pour tests
- **models/** → Modèles séparés
- **views/** → Vue structurée en sous-dossiers

---

## Dossier "reservations" (Projet Django principal)
Contient la configuration principale de Django.

### Fichiers :
- **__init__.py** → Initialise le package
- **asgi.py** → Configuration du serveur ASGI
- **settings.py** → Paramètres globaux (DB, apps, middleware…)
- **urls.py** → Routes principales du projet
- **wsgi.py** → Configuration du serveur WSGI

---

# 🐳 5. Lancer le Projet avec Docker

## Étape 1 : Construire et lancer les conteneurs
```bash
docker compose up --build
```

## Étape 2 : Appliquer les migrations
```bash
docker compose exec web python manage.py migrate
```

## Étape 3 : Créer un superutilisateur
```bash
docker compose exec web python manage.py createsuperuser
```

---

# 🌍 6. Accéder au Projet dans le Navigateur
Une fois Docker lancé, ouvrez :
```
http://localhost:8000
```
Panneau d’administration :
```
http://localhost:8000/admin
```

Si tout est correct, la page d’accueil Django s’affichera.
