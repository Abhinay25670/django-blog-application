# 📝 Django Blog Management System

A full-featured Django-based blogging platform designed with role-based access control, secure authentication, and content management capabilities. The application supports multiple user roles, media handling, commenting, and search functionality, making it suitable for real-world blogging or CMS use cases.

![Django](https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![SQLite](https://img.shields.io/badge/SQLite-07405E?style=for-the-badge&logo=sqlite&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white)

## 🚀 Features

### 🔐 Authentication & Authorization
- User authentication using Django's built-in auth system
- Role-based access using Django Groups & Permissions
- Separate access levels for:
  - **Admin** - Full system access
  - **Manager** - Content moderation & analytics
  - **Editor** - Edit and review posts
  - **Author** - Create and manage own posts

### ✍️ Blog Management
- Complete CRUD operations for blog posts
- Automatic unique slug generation
- Draft and published post handling
- Category-based blog organization
- Rich content management

### 💬 Commenting System
- Authenticated users can add comments
- Permission-based moderation
- Secure handling of user input
- Comment threading support

### 🖼 Media Handling
- Image uploads for blog posts
- Proper media storage and configuration
- Optimized rendering in templates
- Secure file validation

### 🔍 Search Functionality
- Keyword-based blog search
- Query persistence for better UX
- Search across titles and content

### 📊 Role-Based Dashboards
- Dedicated dashboards for Managers and Editors
- Blog analytics and content overview
- Permission-aware UI rendering

## 🛠 Tech Stack

| Technology | Purpose |
|------------|---------|
| **Django** | Backend framework |
| **Python 3.x** | Programming language |
| **SQLite** | Database (default) |
| **Bootstrap** | Frontend styling |
| **HTML/CSS** | Templates & styling |
| **Django Auth** | Authentication system |

## 📂 Project Structure

```
django-blog-application/
│
├── blog/                      # Main blog application
│   ├── migrations/           # Database migrations
│   ├── models.py             # Blog, Category, Comment models
│   ├── views.py              # View functions/classes
│   ├── urls.py               # URL routing
│   ├── forms.py              # Django forms
│   └── admin.py              # Admin panel configuration
│
├── users/                     # User management app
│   ├── models.py             # User profile models
│   ├── views.py              # Auth views
│   └── forms.py              # User forms
│
├── templates/                 # HTML templates
│   ├── base.html             # Base template
│   ├── blog/                 # Blog templates
│   └── users/                # User templates
│
├── static/                    # Static files
│   ├── css/                  # Stylesheets
│   ├── js/                   # JavaScript files
│   └── images/               # Static images
│
├── media/                     # User-uploaded files
│   └── blog_images/          # Blog post images
│
├── manage.py                  # Django management script
├── requirements.txt           # Python dependencies
├── db.sqlite3                # SQLite database
└── README.md                 # This file
```

## ⚙️ Installation & Setup

### Prerequisites
- Python 3.8 or higher
- pip (Python package manager)
- Git

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/Abhinay25670/django-blog-application.git
cd django-blog-application
```

### 2️⃣ Create Virtual Environment

**Linux / macOS:**
```bash
python3 -m venv venv
source venv/bin/activate
```

**Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```

### 3️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

### 4️⃣ Configure Environment Variables (Optional)

Create a `.env` file in the project root:

```env
SECRET_KEY=your-secret-key-here
DEBUG=True
ALLOWED_HOSTS=localhost,127.0.0.1
DATABASE_URL=sqlite:///db.sqlite3
```

### 5️⃣ Apply Database Migrations

```bash
python manage.py makemigrations
python manage.py migrate
```

### 6️⃣ Create Superuser

```bash
python manage.py createsuperuser
```

Follow the prompts to set up your admin account.

### 7️⃣ Create User Groups & Permissions

```bash
python manage.py shell
```

Then run:

```python
from django.contrib.auth.models import Group, Permission
from django.contrib.contenttypes.models import ContentType
from blog.models import Post

# Create groups
admin_group = Group.objects.create(name='Admin')
manager_group = Group.objects.create(name='Manager')
editor_group = Group.objects.create(name='Editor')
author_group = Group.objects.create(name='Author')

# Assign permissions (example)
content_type = ContentType.objects.get_for_model(Post)
permissions = Permission.objects.filter(content_type=content_type)

admin_group.permissions.set(permissions)
manager_group.permissions.set(permissions)
# Add specific permissions for other groups as needed

exit()
```

### 8️⃣ Load Sample Data (Optional)

```bash
python manage.py loaddata sample_data.json
```

### 9️⃣ Run the Development Server

```bash
python manage.py runserver
```

Access the application at: **http://127.0.0.1:8000/**

Admin panel: **http://127.0.0.1:8000/admin/**

## 🔑 User Roles & Permissions

| Role | Capabilities |
|------|--------------|
| **Admin** | Full system access, user management, all CRUD operations |
| **Manager** | Content moderation, analytics, approve/reject posts |
| **Editor** | Edit and review all posts, manage comments |
| **Author** | Create and manage own posts, basic publishing |

Permissions are enforced using Django's built-in Groups and Permissions system with custom authorization logic in views.

## 🧪 Running Tests

```bash
python manage.py test
```

For coverage report:

```bash
coverage run --source='.' manage.py test
coverage report
```

## 📌 Future Enhancements

- [ ] REST API using Django REST Framework
- [ ] Pagination & caching for improved performance
- [ ] Rich text editor (CKEditor / TinyMCE integration)
- [ ] Like & reaction system for posts
- [ ] Social media integration (share buttons)
- [ ] Email notifications for comments
- [ ] Advanced search with filters
- [ ] Tag system for posts
- [ ] Multi-language support (i18n)
- [ ] SEO optimization features
- [ ] Docker deployment configuration
- [ ] AWS/Heroku deployment guides
- [ ] Newsletter subscription system
