# 🎓 EduTrack — Academic Management System

<div align="center">
  
  <!-- ![Python](https://img.shields.io/badge/Python-3.12+-3776AB?style=for-the-badge&logo=python&logoColor=white)
  ![Django](https://img.shields.io/badge/Django-5.2-092E20?style=for-the-badge&logo=django&logoColor=white)
  ![MySQL](https://img.shields.io/badge/MySQL-8.0-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
   -->
  <h3>Modern Educational Platform with Smart Campus Integration</h3>
  <p><i>Full-stack academic management system featuring weighted grading, real-time analytics, and IoT-ready infrastructure</i></p>
  
</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Key Features](#-key-features)
- [Technology Stack](#-technology-stack)
- [Installation](#-installation)
- [Usage](#-usage)
- [Architecture](#-architecture)
- [Database Schema](#-database-schema)
- [Security](#-security)
- [Performance](#-performance)
- [Future Enhancements](#-future-enhancements)
- [Author](#-author)

---

## 🎯 Overview

**EduTrack** is a comprehensive academic management system designed to streamline educational processes for universities and colleges. Built with Django 5.2 and MySQL, it provides a complete solution for managing students, teachers, courses, schedules, grades, and attendance.

### Problem Statement

Traditional academic management systems often lack:
- Transparent and fair grading mechanisms
- Real-time performance analytics
- Flexible schedule management
- Modern, intuitive user interfaces
- Integration capabilities with IoT devices

### Solution

EduTrack addresses these challenges by providing:
- **Bayesian Weighted Rating System**: Fair and objective student performance evaluation
- **Role-Based Dashboards**: Customized interfaces for administrators, teachers, and students
- **Dynamic Schedule Builder**: Flexible timetable creation and management
- **Real-Time Analytics**: Comprehensive performance tracking and reporting
- **IoT Integration**: Ready for RFID-based attendance tracking with ESP32 hardware
- **Modern UI/UX**: Glassmorphism design with smooth animations and responsive layout

---

## ✨ Key Features

### 👨‍💼 Administrator Features

- **User Management**
  - CRUD operations for students, teachers, and administrators
  - Bulk user import/export via CSV
  - Role-based access control
  - User activity tracking

- **Academic Structure**
  - Study group management with year tracking
  - Subject catalog with course codes
  - Teaching assignment coordination
  - Classroom resource allocation

- **Schedule Management**
  - Weekly schedule templates
  - Automated lesson generation
  - Classroom conflict detection
  - Multi-view schedule display (Timeline, Classic, Grid)

- **Reporting & Analytics**
  - Student performance reports
  - Attendance statistics
  - Grade distribution analysis
  - CSV export functionality

### 👨‍🏫 Teacher Features

- **Interactive Grade Book**
  - Real-time grade entry with inline editing
  - Multiple evaluation types (Lectures, Labs, Exams, Projects)
  - Configurable weight percentages per evaluation type
  - Automatic GPA calculation using Bayesian averaging
  - Teacher comments and feedback

- **Attendance Management**
  - Quick absence marking with reason codes
  - Respectful vs. non-respectful absence tracking
  - Attendance statistics per student
  - Weekly and monthly attendance reports

- **Lesson Management**
  - Topic documentation for each lesson
  - Lesson history and archives
  - Performance trends visualization
  - Student participation tracking

- **Live Mode**
  - Random student selection for oral examinations
  - Quick grading interface
  - Timer for timed assessments
  - Real-time class engagement tools

- **Evaluation Configuration**
  - Custom evaluation type creation
  - Weight distribution (e.g., Midterm: 30%, Final: 50%, Labs: 20%)
  - Weight validation (ensures total ≤ 100%)
  - Per-course evaluation customization

### 👨‍🎓 Student Features

- **Personal Dashboard**
  - iOS-style modular interface
  - GPA overview with trend charts
  - Attendance rate visualization
  - Upcoming lessons calendar
  - Performance analytics

- **Grade Transparency**
  - Complete grade history by subject
  - Detailed breakdown by evaluation type
  - Teacher comments and feedback
  - Weighted score calculations
  - Grade distribution comparisons

- **Attendance Tracking**
  - Detailed absence records
  - Absence reason documentation
  - Attendance percentage by subject
  - Monthly attendance calendar

- **Schedule Access**
  - Personal weekly schedule
  - Classroom locations
  - Teacher contact information
  - Lesson topics and materials

---

## 🛠️ Technology Stack

### Backend
- **Framework**: Django 5.2.7
- **Language**: Python 3.12+
- **Database**: MySQL 8.0 (PostgreSQL compatible)
- **ORM**: Django ORM with query optimization
- **Authentication**: Django Auth with custom User model

### Frontend
- **HTML5**: Semantic markup
- **CSS3**: Custom Glassmorphism design
- **JavaScript**: Vanilla JS with AJAX
- **Charts**: Chart.js for data visualization
- **Icons**: Font Awesome / Custom SVG

### Architecture Patterns
- **Service Layer**: Business logic separation
- **Selector Pattern**: Optimized database queries
- **Repository Pattern**: Data access abstraction
- **Decorator Pattern**: Role-based access control

### Development Tools
- **Version Control**: Git
- **Environment Management**: python-dotenv
- **Database Migrations**: Django migrations
- **Testing**: Django TestCase (unit & integration tests)

### Production Stack
- **Web Server**: Nginx
- **WSGI Server**: Gunicorn
- **Static Files**: WhiteNoise / Nginx
- **Caching**: Redis (optional)
- **Monitoring**: Sentry (optional)

---

## 🚀 Installation

### Prerequisites

- Python 3.12 or higher
- MySQL 8.0 or PostgreSQL 14+
- pip (Python package manager)
- Git

### Step-by-Step Setup

#### 1. Clone the Repository

```bash
git clone https://github.com/SerhiiHodis/EduTrack.git
cd EduTrack
```

#### 2. Create Virtual Environment

```bash
# Windows
python -m venv .venv
.venv\Scripts\activate

# Linux/Mac
python3 -m venv .venv
source .venv/bin/activate
```

#### 3. Install Dependencies

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

#### 4. Configure Database

**MySQL Setup:**
```sql
-- Login to MySQL
mysql -u root -p

-- Create database
CREATE DATABASE edutrack_db CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;

-- Create user (optional)
CREATE USER 'edutrack_user'@'localhost' IDENTIFIED BY 'your_password';
GRANT ALL PRIVILEGES ON edutrack_db.* TO 'edutrack_user'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

**PostgreSQL Setup (Alternative):**
```sql
-- Login to PostgreSQL
psql -U postgres

-- Create database
CREATE DATABASE edutrack_db;

-- Create user (optional)
CREATE USER edutrack_user WITH PASSWORD 'your_password';
GRANT ALL PRIVILEGES ON DATABASE edutrack_db TO edutrack_user;
\q
```

#### 5. Environment Configuration

```bash
# Copy environment template
cp .env.example .env

# Edit .env file with your database credentials
# Windows: notepad .env
# Linux/Mac: nano .env
```

**Example `.env` configuration:**
```env
DEBUG=True
SECRET_KEY=your-secret-key-here
ALLOWED_HOSTS=localhost,127.0.0.1

DB_ENGINE=mysql.connector.django
DB_NAME=edutrack_db
DB_USER=root
DB_PASSWORD=your_password
DB_HOST=localhost
DB_PORT=3306
```

#### 6. Run Database Migrations

```bash
python manage.py migrate
```

#### 7. Create Superuser (Administrator)

```bash
python manage.py createsuperuser
```

Follow the prompts to create an admin account.

#### 8. Populate Sample Data (Optional)

```bash
python populate_db.py
```

This creates:
- 5 study groups
- 20 subjects
- 10 teachers
- 40 students
- Teaching assignments
- Schedule templates
- Sample lessons with grades and attendance

**Test Credentials:**
- Teacher: `teacher1@example.com` / `password`
- Student: `student1@example.com` / `password`

#### 9. Collect Static Files (Production)

```bash
python manage.py collectstatic
```

#### 10. Run Development Server

```bash
python manage.py runserver
```

Access the application at: `http://localhost:8000`

---

## 📖 Usage

### First-Time Setup

1. **Login as Administrator**
   - Navigate to `http://localhost:8000/admin/`
   - Use superuser credentials created in step 7

2. **Create Academic Structure**
   - Add study groups (e.g., CS-101, CS-102)
   - Add subjects (e.g., Mathematics, Programming)
   - Create teacher accounts
   - Create student accounts and assign to groups

3. **Configure Teaching Assignments**
   - Assign teachers to subjects and groups
   - Configure evaluation types and weights

4. **Build Schedule**
   - Create weekly schedule templates
   - Assign classrooms and time slots
   - Generate lessons from templates

### Daily Operations

#### As a Teacher:
1. Login at `http://localhost:8000`
2. Navigate to "Teacher Journal"
3. Select subject and group
4. Enter grades and mark attendance
5. Add lesson topics and comments

#### As a Student:
1. Login at `http://localhost:8000`
2. View personal dashboard
3. Check grades and attendance
4. Review schedule and upcoming lessons

#### As an Administrator:
1. Login to admin panel
2. Manage users and academic structure
3. Generate reports
4. Monitor system activity

---

## 🏗️ Architecture

### System Architecture

```
┌─────────────────────────────────────┐
│      Presentation Layer             │
│  (Templates, CSS, JavaScript)       │
└──────────────┬──────────────────────┘
               │
┌──────────────▼──────────────────────┐
│      Application Layer              │
│    (Views, Forms, URLs)             │
└──────────────┬──────────────────────┘
               │
┌──────────────▼──────────────────────┐
│       Business Layer                │
│  (Services, Selectors, Models)      │
└──────────────┬──────────────────────┘
               │
┌──────────────▼──────────────────────┐
│         Data Layer                  │
│     (MySQL/PostgreSQL)              │
└─────────────────────────────────────┘
```

### Design Patterns

**1. Service Layer Pattern**
- Encapsulates business logic
- Example: `grading_service.py` handles GPA calculations

**2. Selector Pattern**
- Optimizes database queries
- Uses `select_related()` and `prefetch_related()`
- Prevents N+1 query problems

**3. Decorator Pattern**
- Role-based access control
- Example: `@role_required('TEACHER')`

**4. Template Method Pattern**
- Reusable base templates
- DRY principle for UI components

---

## 💾 Database Schema

### Core Models

#### User (Custom Django Auth)
```python
- email (unique, primary identifier)
- full_name
- role (ADMIN, TEACHER, STUDENT)
- group (FK to StudyGroup, for students)
- password (hashed with PBKDF2)
- created_at, updated_at
```

#### StudyGroup
```python
- name (e.g., "CS-101")
- year (academic year)
- students (reverse FK)
```

#### Subject
```python
- name (e.g., "Mathematics")
- code (unique identifier)
- description
```

#### TeachingAssignment
```python
- teacher (FK to User)
- subject (FK to Subject)
- group (FK to StudyGroup)
- academic_year
- evaluation_types (reverse FK)
```

#### EvaluationType
```python
- name (e.g., "Midterm Exam")
- weight_percent (0-100)
- teaching_assignment (FK)
- is_active
```

#### LessonSession
```python
- group (FK to StudyGroup)
- subject (FK to Subject)
- teacher (FK to User)
- date, start_time, end_time
- classroom (FK to Classroom)
- topic
- evaluation_type (FK)
- max_points
```

#### StudentPerformance
```python
- student (FK to User)
- lesson (FK to LessonSession)
- earned_points (0-100)
- absence (FK to AbsenceReason, nullable)
- teacher_comment
- created_at
```

#### AbsenceReason
```python
- code (e.g., "Н", "Хв", "ПП")
- description
- is_respectful (boolean)
```

### Relationships

- One User can have many StudentPerformance records
- One LessonSession can have many StudentPerformance records
- One TeachingAssignment can have many EvaluationType records
- One StudyGroup can have many Students (Users)
- One Teacher (User) can have many TeachingAssignments

---

## 🔒 Security

### Authentication & Authorization

- **Password Security**: PBKDF2 hashing with salt
- **Session Management**: Django session framework
- **Role-Based Access**: Custom decorator `@role_required()`
- **CSRF Protection**: Built-in Django middleware
- **XSS Prevention**: Template auto-escaping

### Data Protection

- **Environment Variables**: Sensitive data in `.env` file
- **SQL Injection Prevention**: Django ORM parameterized queries
- **Input Validation**: Django Forms with validators
- **Secure Cookies**: HTTPOnly and Secure flags (production)

### Production Security Checklist

- ✅ `DEBUG = False`
- ✅ Strong `SECRET_KEY`
- ✅ `ALLOWED_HOSTS` configured
- ✅ HTTPS enabled (SSL certificate)
- ✅ Database credentials secured
- ✅ Static files served securely
- ✅ Regular security updates

---

## ⚡ Performance

### Query Optimization

**Problem: N+1 Queries**
```python
# BAD: Triggers N queries
for performance in performances:
    print(performance.lesson.subject.name)  # Query per iteration
```

**Solution: Prefetch Related**
```python
# GOOD: Single query with JOIN
performances = StudentPerformance.objects.select_related(
    'lesson__subject',
    'evaluation_type'
).all()
```

### Database Indexing

- Foreign keys automatically indexed
- Custom indexes on frequently queried fields
- Composite indexes for multi-column queries

### Caching Strategy (Future)

- Page-level caching for dashboards
- Query-level caching for rankings
- Template fragment caching for navigation

### Performance Metrics

- Average page load: < 200ms
- Database query time: < 50ms
- Supports 1000+ concurrent users (with proper infrastructure)

---

## 🔌 IoT Integration (Future Enhancement)

### ESP32 + RFID System

**Hardware Components:**
- ESP32 microcontroller
- RC522 RFID reader
- LED indicators (green/red)
- Buzzer for feedback

**Workflow:**
1. Student scans RFID card at classroom entrance
2. ESP32 reads card UID
3. Sends HTTP POST to Django API endpoint
4. Backend validates student and lesson
5. Marks attendance automatically
6. Returns success/failure to ESP32
7. LED and buzzer provide feedback

**Testing:**
```bash
python simulate_rfid.py
# Enter card UID to simulate scan
```

**API Endpoint (Future):**
```
POST /api/card-scan/
Body: {"uid": "A1B2C3D4"}
Response: {"status": "success", "message": "Attendance marked"}
```

---

## 🚀 Future Enhancements

### Planned Features

1. **RESTful API**
   - Django REST Framework integration
   - JWT authentication
   - Mobile app support

2. **Real-Time Updates**
   - WebSocket integration (Django Channels)
   - Live grade notifications
   - Real-time attendance updates

3. **Advanced Analytics**
   - Machine learning for performance prediction
   - Student risk identification
   - Personalized learning recommendations

4. **Mobile Application**
   - React Native companion app
   - Push notifications
   - Offline mode support

5. **File Management**
   - Assignment upload/download
   - Document sharing
   - Plagiarism detection

6. **Communication Module**
   - Internal messaging system
   - Email notifications
   - SMS alerts for absences

7. **Blockchain Certificates**
   - Immutable academic records
   - Verifiable diplomas
   - Transcript authentication

---

## 📊 Project Statistics

- **Total Lines of Code**: ~13,000+
- **Models**: 15+ database models
- **Views**: 40+ view functions
- **Templates**: 25+ HTML templates
- **Test Coverage**: Unit tests for core functionality
- **Development Time**: 6+ months

---

## 🤝 Contributing

This is a graduation project, but contributions and suggestions are welcome!

### How to Contribute

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Code Style

- Follow PEP 8 for Python code
- Use meaningful variable and function names
- Add docstrings to functions and classes
- Write unit tests for new features

---

## 👨‍💻 Author

**Serhii Hodis** — Graduation Project 2026

- 📧 Email: serghod@icloud.com
- 💼 LinkedIn: https://www.linkedin.com/in/serhii-hodis-410a32395
- 🐙 GitHub: https://github.com/SerhiiHodis

---

## 🙏 Acknowledgments

- **Django Framework** for robust backend infrastructure
- **Chart.js** for beautiful data visualizations
- **MySQL** for reliable data persistence
- **Open-source community** for inspiration and tools
- **My instructors** for guidance and support

---

<div align="center">
  <p><i>Built with ❤️ for modern education</i></p>
  <p><b>EduTrack</b> — Empowering education through technology</p>
  
  ⭐ Star this repository if you find it helpful!
</div>
