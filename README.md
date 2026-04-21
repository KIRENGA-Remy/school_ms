 🏫 School Management System

A comprehensive school management system built with Laravel 11.x, MySQL, and Tailwind CSS. This system manages students, teachers, subjects, enrollments, and academic results efficiently.

## 📋 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Installation](#installation)
- [Database Schema](#database-schema)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Contributing](#contributing)
- [License](#license)

## ✨ Features

### 👨‍🎓 Student Management
- Add, edit, delete student records
- Track student personal information (name, age, gender, admission number)
- View student enrollment history

### 👨‍🏫 Teacher Management
- Manage teacher profiles
- Assign teachers to subjects
- Track teacher specialization

### 📚 Subject Management
- Create and manage subjects
- Assign subjects to teachers
- Categorize subjects (Core, Elective, Practical)

### 📝 Enrollment Management
- Enroll students in subjects
- Track enrollment dates and academic years
- Prevent duplicate enrollments

### 📊 Results Management
- Record student grades per subject per term
- Automatic grade calculation based on marks
- View student transcripts

## 🛠 Tech Stack

| Technology | Version | Purpose |
|------------|---------|---------|
| Laravel | 11.x | Backend Framework |
| MySQL | 8.0+ | Database |
| Tailwind CSS | 3.x | Frontend Styling |
| PHP | 8.2+ | Programming Language |
| Composer | 2.x | Dependency Manager |
| Node.js | 20.x | Asset Compilation |

## 🚀 Installation

### Prerequisites

- PHP >= 8.2
- Composer
- MySQL >= 8.0
- Node.js & NPM

### Step-by-Step Setup

```bash
# 1. Clone the repository
git clone https://github.com/KIRENGA-Remy/school_ms.git
cd school_ms

# 2. Install PHP dependencies
composer install

# 3. Install NPM dependencies
npm install

# 4. Copy environment file
cp .env.example .env

# 5. Generate application key
php artisan key:generate

# 6. Configure database in .env file
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=school_management_system_laravel
DB_USERNAME=root
DB_PASSWORD=

# 7. Run migrations
php artisan migrate

# 8. Seed the database (optional)
php artisan db:seed

# 9. Compile assets
npm run build

# 10. Start the development server
php artisan serve
📊 Database Schema
Tables Structure
Table	Description	Key Fields
students	Student information	id, first_name, last_name, admission_number
teachers	Teacher profiles	id, first_name, last_name, email
subjects	Course subjects	id, subject_code, subject_name, category
enrollments	Student-subject enrollments	id, student_id, subject_id, academic_year
results	Student grades	id, enrollment_id, term, marks, grade
Entity Relationship Diagram
text
┌─────────────┐     ┌──────────────┐     ┌─────────────┐
│  students   │────<│ enrollments  │>────│  subjects   │
└─────────────┘     └──────────────┘     └─────────────┘
                           │
                           │
                           ▼
                    ┌─────────────┐
                    │   results   │
                    └─────────────┘
💻 Usage
Common Operations
php
// Get all students with their enrollments
$students = Student::with('enrollments.subject')->get();

// Get student results for a specific term
$results = Result::where('enrollment_id', $enrollmentId)
                 ->where('term', $term)
                 ->get();

// Calculate student average
$average = Result::where('enrollment_id', $enrollmentId)
                 ->avg('marks');
🔌 API Endpoints
Method	Endpoint	Description
GET	/api/students	List all students
POST	/api/students	Create new student
GET	/api/students/{id}	Get student details
PUT	/api/students/{id}	Update student
DELETE	/api/students/{id}	Delete student
GET	/api/subjects	List all subjects
POST	/api/enrollments	Enroll student in subject
GET	/api/results/{studentId}	Get student results
🧪 Running Tests
bash
# Run all tests
php artisan test

# Run specific test suite
php artisan test --filter=StudentTest
📁 Project Structure
text
school_management_system/
├── app/
│   ├── Http/
│   │   ├── Controllers/     # Application controllers
│   │   └── Middleware/      # Request middleware
│   └── Models/              # Eloquent models
├── database/
│   ├── migrations/          # Database migrations
│   └── seeders/             # Database seeders
├── routes/
│   ├── web.php              # Web routes
│   └── api.php              # API routes
├── resources/
│   └── views/               # Blade templates
└── tests/                   # Feature & unit tests
🤝 Contributing
Fork the repository

Create your feature branch (git checkout -b feature/amazing-feature)

Commit your changes (git commit -m 'Add amazing feature')

Push to the branch (git push origin feature/amazing-feature)

Open a Pull Request

Coding Standards
Follow PSR-12 coding standards

Write tests for new features

Document your code with PHPDoc blocks

Keep pull requests focused on a single feature

📄 License
This project is open-sourced software licensed under the MIT license.

👨‍💻 Author
Remy Claudien GITORI

GitHub: @KIRENGA-Remy

Email: gitoliremy@gmail.com

🙏 Acknowledgments
Laravel community for the amazing framework

All contributors and testers