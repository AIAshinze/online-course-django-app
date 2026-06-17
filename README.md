# Online Course Django App

A comprehensive Django-based online learning management system that enables instructors to create and manage courses with lessons and assessments, while providing learners with the ability to enroll, view course content, and take exams.

## Features

### Course Management

- Create and manage multiple online courses
- Add instructors and track learner enrollments
- Organize course content into structured lessons
- Support for course images and detailed descriptions

### Assessment System

- Create multiple-choice exam questions for courses
- Define correct answers for each question
- Track learner submissions and exam attempts
- Calculate scores based on correct answers

### Learner Features

- User registration and authentication
- Enroll in available courses
- View course lessons and content
- Take exams with immediate scoring
- View detailed exam results with answer feedback
- Retake exams to improve scores

### Admin Interface

- Manage courses, lessons, questions, and choices through Django admin
- Inline editing for related models
- User-friendly admin dashboard

## Technology Stack

- **Framework**: Django 4.2.3
- **Database**: SQLite (default)
- **Frontend**: Bootstrap 4.5.2
- **Image Processing**: Pillow

## Installation & Setup

### Prerequisites

- Python 3.8+
- pip package manager

### Installation Steps

1. Clone the repository:

```bash
git clone <repository-url>
cd online-course-django-app
```

2; Install dependencies:

```bash
pip install -r requirements.txt
```

3; Create migrations and apply them:

```bash
python manage.py makemigrations
python manage.py migrate
```

4; Create a superuser account for admin access:

```bash
python manage.py createsuperuser
```

5; Run the development server:

```bash
python manage.py runserver
```

6; Access the application:

- Main app: <http://localhost:8000/onlinecourse/>
- Admin panel: <http://localhost:8000/admin/>

## Project Structure

```text
online-course-django-app/
├── myproject/              # Django project configuration
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│   └── asgi.py
├── onlinecourse/           # Main application
│   ├── models.py           # Database models (Course, Lesson, Question, Choice, etc.)
│   ├── views.py            # View functions and classes
│   ├── urls.py             # URL routing
│   ├── admin.py            # Admin configuration
│   ├── migrations/         # Database migrations
│   └── templates/          # HTML templates
│       └── onlinecourse/
│           ├── course_list_bootstrap.html
│           ├── course_detail_bootstrap.html
│           ├── exam_result_bootstrap.html
│           ├── user_login_bootstrap.html
│           └── user_registration_bootstrap.html
├── static/                 # Static files (CSS, JS, images)
├── manage.py              # Django management script
└── requirements.txt       # Python dependencies
```

## Models

### Course

- Represents an online course
- Contains lessons, questions, and learner enrollments
- Tracks total enrollment count

### Lesson

- Represents course content sections
- Contains order and detailed content

### Question

- Represents exam questions
- Associated with a course
- Has a grade/point value

### Choice

- Represents answer options for questions
- Can be marked as correct or incorrect

### Submission

- Represents a learner's exam submission
- Tracks selected answers
- Links to course enrollment

### Enrollment

- Represents a learner's registration in a course
- Tracks enrollment date and mode (audit, honor, beta)

## Usage

### For Instructors

1. Log in to the admin panel
2. Create a new course with title, description, and image
3. Add lessons to the course
4. Create exam questions and answer choices
5. Publish the course for learners

### For Learners

1. Register for an account
2. Browse available courses
3. Enroll in desired courses
4. View course lessons and content
5. Take exams when ready
6. View results and retake if needed

## Deployment

The application can be deployed to cloud platforms like IBM Cloud using the provided configuration files:

- `Procfile`: Application entry point for cloud deployment
- `manifest.yml`: Cloud deployment configuration
- `runtime.txt`: Python version specification

## Contributing

Contributions are welcome! Please feel free to submit pull requests or report issues.

## License

This project is part of an IBM Skills Network course.

## Acknowledgments

- IBM Skills Network for the course structure and guidelines
- Django documentation and community support
