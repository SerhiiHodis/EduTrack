# 🎓 EduPixels — Academic Management System

<div align="center">
  <h3>🚀 Status: Production-Ready MVP</h3>
  <p><i>Modern educational platform with IoT integration for smart campus automation</i></p>
  
  ![Python](https://img.shields.io/badge/Python-3.12+-blue.svg)
  ![Django](https://img.shields.io/badge/Django-5.2-green.svg)
  ![MySQL](https://img.shields.io/badge/MySQL-8.0-orange.svg)
  ![License](https://img.shields.io/badge/License-MIT-yellow.svg)
</div>

---

## 📖 Overview

**EduPixels** is a comprehensive academic management system designed to automate and streamline educational processes. Built as a graduation project, it focuses on transparent grading, deep analytics, and future integration with IoT hardware for smart campus solutions.

The platform implements a **Bayesian Weighted Rating** system for objective student performance evaluation and features a modern glassmorphism UI design.

### 🎯 Key Features

- **Role-Based Access Control**: Separate interfaces for administrators, teachers, and students
- **Weighted Grading System**: Customizable evaluation types with configurable weights
- **Advanced Analytics**: Bayesian average calculations for fair student rankings
- **Real-Time Attendance**: IoT-ready infrastructure for RFID-based check-ins
- **Comprehensive Reporting**: CSV exports, absence reports, and performance analytics
- **Responsive Design**: Premium glassmorphism UI with smooth animations

---

## 🏗️ Architecture

### Technology Stack

- **Backend**: Python 3.12+ / Django 5.2
- **Database**: MySQL 8.0 / PostgreSQL (compatible)
- **Frontend**: Vanilla CSS (Glassmorphism), AJAX, Chart.js
- **Hardware Interface**: ESP32 + RFID (RC522) integration ready
- **Security**: Django Auth, role-based permissions, environment-based configuration

### Core Models

```
User → StudyGroup → TeachingAssignment → Subject
                  ↓
              LessonSession → StudentPerformance
                  ↓
              EvaluationType (weighted)
```

---

## 🚀 Quick Start

### Prerequisites

- Python 3.12 or higher
- MySQL 8.0 or PostgreSQL
- pip (Python package manager)

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository_url>
   cd Django
   ```

2. **Create virtual environment**
   ```bash
   python -m venv .venv
   .venv\Scripts\activate  # Windows
   source .venv/bin/activate  # Linux/Mac
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment**
   ```bash
   cp .env.example .env
   # Edit .env with your database credentials
   ```

5. **Run migrations**
   ```bash
   python manage.py migrate
   ```

6. **Create superuser**
   ```bash
   python manage.py createsuperuser
   ```

7. **Populate sample data (optional)**
   ```bash
   python populate_db.py
   ```

8. **Start development server**
   ```bash
   python manage.py runserver
   ```

9. **Access the application**
   - Open browser: `http://localhost:8000`
   - Admin panel: `http://localhost:8000/admin`

---

## 👥 User Roles & Capabilities

### 🔧 Administrator
- **User Management**: CRUD operations for students, teachers, and admins
- **Academic Setup**: Manage groups, subjects, and teaching assignments
- **Schedule Management**: Create and modify weekly schedules
- **System Reports**: Access comprehensive analytics and exports
- **Classroom Management**: Configure physical classrooms and resources

### 👨‍🏫 Teacher
- **Grade Book**: Interactive journal with weighted evaluation types
- **Attendance Tracking**: Mark absences with reason codes
- **Lesson Topics**: Document and manage lesson content
- **Performance Analytics**: View student progress and trends
- **Live Mode**: Real-time student selection and quick grading
- **Custom Weights**: Configure evaluation type importance (e.g., Exam: 50%, Lab: 20%)

### 👨‍🎓 Student
- **Personal Dashboard**: iOS-style modular interface with statistics
- **Grade Transparency**: View all grades with teacher comments
- **Attendance History**: Detailed absence tracking and statistics
- **Performance Trends**: Visual charts showing academic progress
- **GPA Calculation**: Real-time weighted average based on Bayesian model

---

## 🔌 IoT Integration (Future Enhancement)

### ESP32 + RFID System

The platform is designed with IoT integration in mind for automated attendance:

- **Hardware**: ESP32 microcontroller + RC522 RFID reader
- **Communication**: MQTT or WebSocket protocol
- **Functionality**: Students/teachers scan RFID cards for automatic check-in
- **Real-Time Sync**: Instant attendance updates in the grade book
- **Testing**: `simulate_rfid.py` script included for development

```python
# Example: RFID simulation
python simulate_rfid.py --card-id STUDENT001 --lesson-id 42
```

---

## 📊 Grading System

### Bayesian Weighted Rating

EduPixels uses a sophisticated grading algorithm that considers:

1. **Evaluation Type Weights**: Different assignment types have configurable importance
2. **Statistical Variance**: Accounts for sample size and distribution
3. **Fair Comparison**: Normalizes scores across different evaluation methods

**Formula**:
```
Weighted_GPA = Σ(score × weight × confidence_factor) / Σ(weight)
```

### Evaluation Types

- Lectures
- Practical Labs
- Seminars
- Midterm Exams
- Final Exams
- Projects
- Custom types (configurable)

---

## 🎨 UI/UX Design

### Design Philosophy

- **Glassmorphism**: Modern frosted-glass aesthetic with backdrop blur
- **Dark Mode**: Eye-friendly interface for extended use
- **Micro-animations**: Smooth transitions and hover effects
- **Responsive Layout**: Mobile-first approach with CSS Grid
- **Accessibility**: WCAG 2.1 compliant color contrasts

### Key Screens

1. **Student Dashboard**: Modular iOS-style tiles with Chart.js visualizations
2. **Teacher Journal**: Interactive table with inline editing
3. **Schedule Builder**: Drag-and-drop interface for timetable creation
4. **Analytics Reports**: Filterable tables with CSV export

---

## 📁 Project Structure

```
Django/
├── edutrack_project/       # Django project settings
│   ├── settings.py         # Configuration
│   ├── urls.py            # URL routing
│   └── wsgi.py            # WSGI entry point
├── main/                   # Main application
│   ├── models.py          # Database models
│   ├── views.py           # Business logic
│   ├── forms.py           # Form validation
│   ├── selectors.py       # Query optimization
│   ├── services/          # Service layer
│   ├── templates/         # HTML templates
│   ├── static/            # CSS, JS, images
│   └── migrations/        # Database migrations
├── manage.py              # Django CLI
├── populate_db.py         # Sample data generator
├── simulate_rfid.py       # IoT testing script
├── requirements.txt       # Python dependencies
└── .env.example           # Environment template
```

---

## 🔒 Security Features

- **Password Hashing**: Django's PBKDF2 algorithm
- **CSRF Protection**: Built-in Django middleware
- **SQL Injection Prevention**: ORM-based queries
- **XSS Protection**: Template auto-escaping
- **Environment Variables**: Sensitive data in `.env` file
- **Role-Based Access**: Decorator-based view protection

---

## 📈 Performance Optimizations

- **Query Optimization**: `select_related()` and `prefetch_related()` to prevent N+1 queries
- **Database Indexing**: Strategic indexes on foreign keys and frequently queried fields
- **Lazy Loading**: Pagination for large datasets
- **Static File Caching**: Browser cache headers for CSS/JS
- **Connection Pooling**: MySQL connection reuse

---

## 🧪 Testing

### Run Tests
```bash
python manage.py test
```

### Coverage Report
```bash
coverage run --source='.' manage.py test
coverage report
```

---

## 📦 Deployment

### Production Checklist

- [ ] Set `DEBUG = False` in settings
- [ ] Configure `ALLOWED_HOSTS`
- [ ] Use production database (MySQL/PostgreSQL)
- [ ] Set strong `SECRET_KEY`
- [ ] Configure static files serving (WhiteNoise/Nginx)
- [ ] Enable HTTPS
- [ ] Set up database backups
- [ ] Configure logging

### Recommended Stack

- **Web Server**: Nginx
- **WSGI Server**: Gunicorn
- **Database**: MySQL 8.0 or PostgreSQL 14+
- **Caching**: Redis (optional)
- **Monitoring**: Sentry for error tracking

---

## 🤝 Contributing

This is a graduation project, but suggestions are welcome:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 👨‍💻 Author

**Graduation Project 2026**

- Portfolio: [Your Portfolio URL]
- LinkedIn: [Your LinkedIn]
- Email: [Your Email]

---

## 🙏 Acknowledgments

- Django Framework for robust backend infrastructure
- Chart.js for beautiful data visualizations
- MySQL for reliable data persistence
- The open-source community for inspiration

---

<div align="center">
  <p><i>Built with ❤️ for modern education</i></p>
  <p><b>EduPixels</b> — Where technology meets academia</p>
</div>
