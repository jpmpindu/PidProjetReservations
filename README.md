# 📘 Reservations Project – Full Documentation

## 🐳 1. Installing Docker
Before running this project, you must install Docker on your system. Below are the installation steps for **Windows**, **Linux**, and **macOS**.

---

## 🪟 1.1 Install Docker on Windows
### Requirements:
- Windows 10/11 Pro, Enterprise, or Education
- Hyper‑V enabled

### Steps:
1. Download Docker Desktop for Windows from the official website.
2. Install it and follow the instructions.
3. Restart your computer.
4. Launch Docker Desktop.

### Start Docker on Windows:
Docker Desktop starts automatically. If not:
```
Start Menu → Docker Desktop
```
Wait until it says **Docker is running**.

---

## 🐧 1.2 Install Docker on Linux
Docker installation depends on your distribution. Example for Ubuntu:

### Steps:
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

### Start Docker on Linux:
```bash
sudo systemctl start docker
sudo systemctl enable docker
```

---

## 🍎 1.3 Install Docker on macOS
### Steps:
1. Download Docker Desktop for macOS from the official website.
2. Drag Docker.app to **Applications**.
3. Launch Docker.
4. Grant necessary security permissions.

### Start Docker on macOS:
Docker starts automatically. If not:
```
Applications → Docker
```
Wait for **Docker is running**.

---

# 🧬 2. Clone the Project
Run the following command:
```bash
git clone https://github.com/jpmpindu/PidProjetReservations.git
cd PidProjetReservations
cd reservations
```

You will now see this file structure.

---

# 🗂️ 3. Project Architecture
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

# 📝 4. File and Folder Explanations

## Root Files
### **.gitignore**
Defines which files Git should ignore.

### **README.md**
Documentation for the project.

### **docker-compose.yml**
Defines services (Django, MySQL, etc.) and how they run together.

### **Dockerfile**
Builds the Django application image.

### **manage.py**
Django command-line tool used to run the server, migrations, etc.

### **.env.example**
Template containing required environment variables. Duplicate it:
```bash
cp .env.example .env
```

---

## The "accounts" App
Handles user management.

### Files:
- **__init__.py** → Marks folder as a Python package
- **admin.py** → Admin configuration
- **apps.py** → Django app configuration
- **models.py** → Database models
- **tests.py** → Unit tests
- **urls.py** → URL routing for this app
- **views.py** → Logic that returns responses

### Folders:
- **forms/** → Django forms (Signup, Login…)
- **migrations/** → Auto-generated migration files
- **templates/** → HTML templates

---

## The "catalogue" App
Handles products, menus, and catalog data.

### Files:
Same structure as `accounts`, plus:
- **fixtures/** → Initial test data
- **models/** → Splitted model files
- **views/** → Structured views folder

---

## The "reservations" Folder (Main Django Project)
Contains core Django configuration.

### Files:
- **__init__.py** → Package initializer
- **asgi.py** → ASGI server configuration
- **settings.py** → Global settings (DB, apps, middleware, templates…)
- **urls.py** → Main project routing
- **wsgi.py** → WSGI server configuration

---

# 🐳 5. Run the Project with Docker

## Step 1: Build and start containers
```bash
docker compose up --build
```

## Step 2: Apply database migrations
```bash
docker compose exec web python manage.py migrate
```

## Step 3: Create a superuser
```bash
docker compose exec web python manage.py createsuperuser
```

---

# 🌍 6. Access the Project in Your Browser
Once Docker is running, open:
```
http://localhost:8000
```
Admin panel:
```
http://localhost:8000/admin
```

If everything is correct, the Django homepage should appear.

---
