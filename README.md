
# 🎓 Erasmus+ Hub

A fully functional web application for managing the Erasmus+ program, developed using the Flask framework.

## 📋 Table of Contents

- [About the Project](#-about-the-project)
- [Features](#-features)
- [Installation](#-installation)
- [Project Structure](#-project-structure)
- [Usage](#-usage)
- [Technologies](#-technologies)
- [API and Routing](#-api-and-routing)
- [Security](#-security)

## 🎯 About the Project

Erasmus+ Hub is a comprehensive system for managing student mobility applications within the Erasmus+ program. The application provides a fully functional interface for both students and administrators, allowing them to manage applications, documents, announcements, and statistics.

## ✨ Features

### 🔐 Authentication and Authorization

- ✅ User registration (students and administrators)
- ✅ User login and logout
- ✅ Different access levels (student/admin)
- ✅ Role-based route protection
- ✅ Password hashing (Werkzeug PBKDF2)
- ✅ Session-based authentication with a 24-hour expiration time

### 👨‍🎓 Student Dashboard

- ✅ Create new mobility applications
- ✅ Upload documents
- ✅ View personal applications
- ✅ Update documents within an application
- ✅ Track document statuses
- ✅ View announcements and news
- ✅ Edit personal profile
- ✅ Download files
- ✅ View administrator comments

### 👨‍💼 Administrator Dashboard

- ✅ Main statistics dashboard
- ✅ Application management (view, approve, reject)
- ✅ Add comments to applications
- ✅ Manage document statuses
- ✅ User management
- ✅ Announcement management (CRUD operations)
- ✅ Detailed statistics
- ✅ Search and filter applications
- ✅ Filter applications by student, status, and search query

### 💾 Database

- ✅ SQLite database
- ✅ Tables: users, applications, documents, application_comments, messages, announcements
- ✅ Automatic migration from JSON files
- ✅ Full CRUD operations for all entities
- ✅ Referential integrity (Foreign Keys)
- ✅ Cascading deletion

### 📊 Statistics

- ✅ Monthly statistics
- ✅ Statistics by mobility type
- ✅ Document statistics
- ✅ Total number of applications and students

## 🚀 Installation

### Requirements

- Python 3.8 or higher
- pip (Python package manager)

### Installation Steps

1. Clone or download the project and navigate to its directory:

   ```bash
   cd erasmus_hub
   ```

2. Create a virtual environment (recommended):

   ```bash
   python -m venv venv
   ```

   **Windows:**

   ```bash
   venv\Scripts\activate
   ```

   **Linux/Mac:**

   ```bash
   source venv/bin/activate
   ```

3. Install the dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Start the application:

   ```bash
   python app.py
   ```

5. Open your browser and navigate to:

   ```text
   http://localhost:5000
   ```

### First Launch

On the first launch, the application automatically:

- Creates the SQLite database (`erasmus_hub.db`)
- Creates all required database tables
- Creates default users (if the database is empty)
- Migrates data from JSON files (if they exist)

## 📁 Project Structure

```text
erasmus_hub/
├── app.py                      # Main Flask application
├── database.py                 # Database initialization and migration
├── models.py                   # Database models
├── config.py                   # Application configuration
├── requirements.txt            # Python dependencies
├── erasmus_hub.db              # SQLite database (created automatically)
├── templates/                  # HTML templates
│   ├── base.html
│   ├── index.html
│   ├── login.html
│   ├── register.html
│   ├── student_dashboard.html
│   ├── student_profile.html
│   ├── student_view_application.html
│   ├── student_announcements.html
│   ├── application_form.html
│   ├── update_documents.html
│   ├── admin_panel.html
│   ├── admin_view_application.html
│   ├── admin_announcement_form.html
│   ├── admin_users.html
│   └── admin_statistics.html
└── static/                     # Static files
    ├── css/
    │   └── styles.css
    └── uploads/                # Uploaded files
```

## 💻 Usage

### Default Users

After the first launch, the following accounts are available:

**Student:**

- Email: `student@example.com`
- Password: `student`

**Administrator:**

- Email: `admin@example.com`
- Password: `admin`

⚠️ **Important:** Change these default credentials before deploying the application to a production environment!

### Document Types

The application supports 7 types of required documents:

1. Curriculum Vitae (in English)
2. Motivation Letter (in English)
3. Transcript of Records certified by the faculty
4. Proposed Study Plan
5. Language Proficiency Certificate
6. Copy of Passport (for international students)
7. Other – Additional supporting documents

### Application Statuses

- **Submitted** – The application has been submitted and is awaiting review.
- **Approved** – The application has been approved by an administrator.
- **Rejected** – The application has been rejected (with a reason provided).

### Document Statuses

- **Submitted** – The document has been uploaded.
- **Under Review** – The document is currently being reviewed.
- **Approved** – The document has been approved.
- **Rejected** – The document has been rejected.

## 🔧 Technologies

- **Flask 3.0.3** – Web framework
- **SQLite** – Database management system
- **Bootstrap 5.3.2** – Frontend framework
- **Werkzeug** – Security and password hashing
- **Jinja2** – Templating engine

## 🛣️ API and Routing

### Public Routes

| Method | Route | Description |
|---|---|---|
| GET | `/` | Home page |
| GET/POST | `/login` | User login |
| GET/POST | `/register` | User registration |
| GET | `/logout` | User logout |

### Student Routes

| Method | Route | Description |
|---|---|---|
| GET | `/student` | Student dashboard |
| GET/POST | `/student/profile` | Student profile |
| GET | `/student/application/<id>` | Application details |
| GET | `/student/announcements` | Announcements |
| GET/POST | `/application` | Create a new application |
| GET/POST | `/student/application/<id>/update-documents` | Update application documents |
| POST | `/applications/<id>/delete` | Delete an application |

### Administrator Routes

| Method | Route | Description |
|---|---|---|
| GET | `/admin` | Administrator dashboard |
| GET | `/admin/applications/<id>` | Application details |
| POST | `/admin/applications/<id>/approve` | Approve an application |
| POST | `/admin/applications/<id>/reject` | Reject an application |
| POST | `/admin/applications/<id>/comment` | Add a comment |
| GET/POST | `/admin/announcements/new` | Create a new announcement |
| GET/POST | `/admin/announcements/<id>/edit` | Edit an announcement |
| POST | `/admin/announcements/<id>/delete` | Delete an announcement |
| GET | `/admin/users` | User management |
| POST | `/admin/users/<email>/delete` | Delete a user |
| POST | `/admin/documents/<id>/update-status` | Update document status |
| GET | `/admin/statistics` | Detailed statistics |

### General Routes

| Method | Route | Description |
|---|---|---|
| GET | `/download/<filename>` | Download a file |

## 🔒 Security

### Implemented Security Measures

- ✅ Password hashing using PBKDF2
- ✅ Route protection using decorators (`@login_required`, `@role_required`)
- ✅ Secure file storage using `secure_filename`
- ✅ Input data validation
- ✅ File access control
- ✅ Session-based authentication with an expiration time

### Production Recommendations

- Change the `SECRET_KEY` in `app.py`
- Use a production-grade database (PostgreSQL, MySQL)
- Enable HTTPS
- Regularly update project dependencies
- Use environment variables to store sensitive information

## 📝 Notes

- The database is created automatically on the first application launch.
- Uploaded files are stored in `static/uploads/`.
- Automatic migration from JSON files is performed at startup (if such files exist).
- All timestamps are stored in UTC.

## 🤝 Support

If you have any questions or encounter any issues, please create an issue in the project's repository.

## 📄 License

This project was created for educational purposes.
