📝 Django Blog Management System

A full-featured Django-based blogging platform designed with role-based access control, secure authentication, and content management capabilities. The application supports multiple user roles, media handling, commenting, and search functionality, making it suitable for real-world blogging or CMS use cases.

🚀 Features
🔐 Authentication & Authorization

User authentication using Django’s built-in auth system

Role-based access using Django Groups & Permissions

Separate access levels for:

Admin

Manager

Editor

Author

✍️ Blog Management

Create, Read, Update, Delete (CRUD) operations for blog posts

Automatic unique slug generation

Draft and published post handling

Category-based blog organization

💬 Commenting System

Authenticated users can add comments

Permission-based moderation

Secure handling of user input

🖼 Media Handling

Image uploads for blog posts

Proper media storage and configuration

Optimized rendering in templates

🔍 Search Functionality

Keyword-based blog search

Query persistence for better UX

📊 Role-Based Dashboards

Dedicated dashboards for Managers and Editors

Blog analytics and content overview

Permission-aware UI rendering

🛠 Tech Stack

Backend: Django (Python)

Frontend: HTML, CSS, Bootstrap

Database: SQLite (default, configurable)

Authentication: Django Auth

Authorization: Django Groups & Permissions

📂 Project Structure
django-blog-application/
│
├── blog/                  # Blog app (models, views, urls)
├── templates/             # HTML templates
├── static/                # CSS, JS, images
├── media/                 # Uploaded media files
├── users/                 # User & role management
├── db.sqlite3             # Database
├── manage.py
└── requirements.txt

⚙️ Installation & Setup
1️⃣ Clone the Repository
git clone https://github.com/Abhinay25670/django-blog-application.git
cd django-blog-application

2️⃣ Create Virtual Environment
python -m venv venv
source venv/bin/activate      # Linux / Mac
venv\Scripts\activate         # Windows

3️⃣ Install Dependencies
pip install -r requirements.txt

4️⃣ Apply Migrations
python manage.py makemigrations
python manage.py migrate

5️⃣ Create Superuser
python manage.py createsuperuser

6️⃣ Run the Server
python manage.py runserver


Access the application at:

http://127.0.0.1:8000/

🔑 Roles & Permissions
Role	Capabilities
Admin	Full system access
Manager	Content moderation & analytics
Editor	Edit and review posts
Author	Create and manage own posts

Permissions are enforced using Django Groups and custom authorization logic.

📌 Future Enhancements

REST API using Django REST Framework

Pagination & caching

Rich text editor (CKEditor / TinyMCE)

Likes & reactions

Deployment with Docker & AWS