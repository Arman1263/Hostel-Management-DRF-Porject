# 🏨 Hostel Management System – Django REST Framework

A role-based **Hostel Management Backend API** built using **Django REST Framework (DRF)** with **JWT authentication**.

This project focuses on **clean backend architecture**, **proper permissions**, and **real-world hostel workflows**.

---

## 🚀 Features

### 🔐 Authentication & Roles
- JWT-based authentication (Login / Refresh)
- Custom User model with roles:
  - **ADMIN**
  - **STUDENT**
  - **WARDEN**

---

### 👨‍💼 Admin Capabilities
- Create **Students** and **Wardens**
- Create Hostels
- Create Rooms under Hostels
- Assign:
  - Students → Rooms
  - Wardens → Hostels
- View all complaints

---

### 🎓 Student Capabilities
- Login using JWT
- Create complaints
- View **only their own complaints**
- Complaint automatically linked to:
  - Student
  - Hostel (via room allocation)

---

### 🧑‍✈️ Warden Capabilities
- View complaints related to **their hostel**
- Update complaint status:
  - OPEN
  - IN_PROGRESS
  - RESOLVED

---

## 🧩 Tech Stack

- **Backend:** Django, Django REST Framework
- **Auth:** Simple JWT
- **Database:** SQLite (development)
- **Permissions:** Custom role-based permissions

---

## 📁 Project Structure

Hostel_Management_DRF/
│
├── accounts/ # Custom user model, auth, roles
├── hostels/ # Hostel & warden-hostel mapping
├── rooms/ # Rooms & student allocation
├── complaints/ # Complaint system
├── common/ # Constants & permissions
├── config/ # Project settings & URLs
├── requirements.txt
└── manage.py


---

## 🔑 API Endpoints Overview

### Auth
- `POST /api/auth/login/`
- `POST /api/auth/refresh/`
- `GET  /api/auth/me/`

### Admin
- `POST /api/auth/create-student/`
- `POST /api/auth/create-warden/`
- `POST /api/hostels/`
- `POST /api/rooms/`
- `POST /api/rooms/allocate/`

### Complaints
- `POST /api/complaints/` → Student
- `GET  /api/complaints/` → Role-based listing
- `PATCH /api/complaints/{id}/` → Warden/Admin

---

## 🛡 Permissions Logic (Important)

| Role     | Can View Complaints | Can Create | Can Update |
|----------|--------------------|------------|------------|
| Admin    | All                | ❌         | ✅ |
| Student  | Own only           | ✅         | ❌ |
| Warden   | Hostel-specific    | ❌         | ✅ |

---

## ⚙️ Setup Instructions

### 1️⃣ Clone Repository
git clone https://github.com/Arman1263/Hostel-Management-DRF-Porject.git
cd Hostel-Management-DRF-Porject

### 2️⃣ Create Virtual Environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

### 3️⃣ Install Dependencies
pip install -r requirements.txt

### 4️⃣ Environment Variables
Create .env file:

SECRET_KEY=your-secret-key
DEBUG=True

### 5️⃣ Run Migrations
python manage.py migrate

### 6️⃣ Create Superuser
python manage.py createsuperuser

### 7️⃣ Run Server
python manage.py runserver
