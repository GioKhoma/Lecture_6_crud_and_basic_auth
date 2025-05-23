# 📚 Lecture 6 – Django: CRUD Operations & Authentication

This Django project demonstrates how to build basic **CRUD functionality** along with **user authentication**, using both built-in and custom tools from Django's auth system.

---

## ✅ Features

- **CRUD for Employees**
  - Add, edit, delete, and list employees
  - Template-driven forms with validation
  - Action buttons for edit/delete in tables

- **User Authentication**
  - Login with `AuthenticationForm`
  - Register with `UserCreationForm`
  - Use of `authenticate`, `login`, `logout` from `django.contrib.auth`

- **Custom User Model**
  - Extended user model using `AUTH_USER_MODEL = "users.CustomUser"`
  - Custom login and registration forms

- **Messages Framework**
  - Success and error feedback via `django.contrib.messages`

---

## 🛠️ Project Setup

### 1. Templates Directory

Custom templates are stored in a **top-level `templates/` folder**, not inside individual apps.

In `settings.py`, this is configured as:

```python
TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [BASE_DIR / 'templates'],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]
```

Includes a global `base.html` file used across the app.

### 2. Authentication Settings

In `settings.py`, the following authentication-related settings are used:

```python
AUTH_USER_MODEL = "users.CustomUser"
LOGIN_URL = '/users/login_user'
```

These allow for custom user handling and proper redirection when `@login_required` is used.

---

## 📁 Project Structure (Highlights)

```
Lecture_6_Django/
├── manage.py
├── templates/
│   ├── base.html
│   └── registration/
│       └── login.html
├── users/
│   ├── models.py        # CustomUser model
│   ├── forms.py         # Custom auth forms
│   ├── views.py         # login_user, register_user

and other apps
```

---

## 🚀 Running the Project

```bash
python manage.py makemigrations
python manage.py migrate
python manage.py runserver
```

Visit `http://localhost:8000/` to access the app.

---

## 📝 Notes

- All views requiring authentication use `@login_required`
- Built-in forms (`AuthenticationForm`, `UserCreationForm`) are used for login/register
- Feedback messages shown using `messages.success` and `messages.error`
- Templates are cleanly organized and extend from a shared `base.html`

---

## 👤 Author

Lecture prepared by Giorgi Khomasuridze
