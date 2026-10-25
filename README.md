# Our Coffee — Django Cafe Website

A Django website for a cafe, with menu pages, user accounts, table reservations, and order records. The project uses server-rendered Django templates, custom CSS, SQLite, and Django's built-in authentication.

## Features

- Cafe landing page with about and contact sections
- Account registration, login, and logout
- Menu item model with categories, descriptions, prices, and uploaded images
- Signed-in users can submit orders and table reservations
- Personal dashboard for viewing a user's orders and reservations
- Django Admin pages for managing menu items, orders, and reservations
- Static image and stylesheet assets, plus local media uploads

> **Scope:** The order form creates an order record directly. There is no shopping cart, online payment, or order fulfillment integration.

## Technology

- Python
- Django 5.1.6
- SQLite
- HTML and Django templates
- CSS
- Pillow for image uploads

## Getting started

### Requirements

- Python 3.10 or later (Python 3.11 is recommended)
- Git

### 1. Clone the repository

```bash
git clone https://github.com/niusha-adib20/cafe_site.git
cd cafe_site
```

### 2. Create and activate a virtual environment

**Windows PowerShell:**

```powershell
py -3.11 -m venv .venv
.\.venv\Scripts\Activate.ps1
```

**macOS / Linux:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies and apply database migrations

```bash
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python manage.py migrate
```

The development configuration uses SQLite at `db.sqlite3`.

### 4. Create an admin account (optional)

```bash
python manage.py createsuperuser
```

Use the Django Admin to add or manage menu items and inspect orders and reservations.

### 5. Start the development server

```bash
python manage.py runserver
```

Open [http://127.0.0.1:8000/](http://127.0.0.1:8000/) in your browser. The Django Admin is available at [http://127.0.0.1:8000/admin/](http://127.0.0.1:8000/admin/).

## Pages and routes

| Page or action | URL | Access |
|---|---|---|
| Home | `/` | Public |
| Menu page | `/menu/` | Public |
| Sign in | `/login/` | Public |
| Sign up | `/signUp/` | Public |
| Reservation form | `/reservation/` | Public; sign-in required to submit |
| Submit a reservation | `/orders/reserve/` | Sign-in required |
| Submit an order | `/orders/place_order/` | Sign-in required |
| User dashboard | `/orders/dashboard/` | Sign-in required |
| Django Admin | `/admin/` | Staff account |

The data-backed menu view is also available at `/orders/menu/`. At present, the main `/menu/` route renders the menu template without loading the menu items into its context, so it may appear empty. Menu records can be managed in Django Admin.

## Project structure

```text
cafe_site/
├── cafe/                  # Django settings and root URL configuration
├── accounts/              # Registration, login, and public pages
├── orders/                # Menu items, orders, reservations, and dashboard
├── templates/             # Django HTML templates
├── static/
│   ├── image/             # Static site images
│   └── style/             # Page stylesheets
├── media/menu_items/      # Uploaded menu item images
├── manage.py
├── requirements.txt
└── LICENSE
```

## Current scope and deployment notes

- Orders are stored for the signed-in user and shown in the dashboard. The app does not provide cart management, checkout, payments, or fulfillment.
- The project currently uses a development Django configuration, including `DEBUG = True` and a secret key stored in `cafe/settings.py`. Before deploying, use a new secret key from a secure environment configuration, set `DEBUG = False`, configure `ALLOWED_HOSTS`, and review Django's deployment checklist.
- Uploaded media is stored locally under `media/`; production deployments need persistent storage and appropriate upload validation.
- The existing app test files are placeholders and do not provide feature-level test coverage.

## License

This project is licensed under the [MIT License](LICENSE).
