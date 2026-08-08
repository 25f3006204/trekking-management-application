# Trekking Management Application

A modular, role-based web application built with **Flask**, **Flask-SQLAlchemy**, and **Bootstrap 5**. The platform connects trekking enthusiasts with certified trek leaders and system administrators, providing streamlined route discovery, guide approvals, slot reservations, and dashboard analytics.

---

## Features

### 🔐 Authentication & Security
* **Role-Based Access Control:** Distinct interfaces and privileges for **Admins**, **Staff (Guides)**, and **Users (Trekkers)**.
* **Password Hashing:** Secure password encryption using Werkzeug's PBKDF2/SHA-256 implementation.
* **Staff Approval Workflow:** Newly registered staff accounts require Admin verification before system login is granted.
* **Blacklist Protection:** Banned or blacklisted users/staff are blocked from authenticating.

### 🏔️ Trekker (User) Features
* Search and filter treks by location, name, and difficulty rating.
* Book available trek slots with automatic overbooking and duplicate reservation checks.
* View personal booking history and manage active reservations.
* Cancel bookings with automatic real-time slot restoration.

### 🥾 Staff (Guide) Features
* View assigned treks on a dedicated dashboard.
* Update trek availability statuses (`Open`, `Closed`, `Completed`) and manage slot capacities.

### 🛠️ Admin Features
* Comprehensive metrics dashboard tracking total users, staff, treks, and recent bookings.
* Create, assign, search, and delete trek routes.
* Review, approve, or reject pending staff registration applications.
* Database safety cascades for removing staff or treks without breaking relational foreign keys.

---

## Tech Stack

* **Language:** Python 3.x
* **Backend Framework:** Flask
* **Database / ORM:** SQLite / Flask-SQLAlchemy
* **Authentication:** Flask-Login
* **Front-End:** HTML5, Jinja2 Templates, Bootstrap 5, Custom CSS
* **Security:** Werkzeug Security (`generate_password_hash`, `check_password_hash`)

---

## Project Structure

```text
.
├── app.py              # Application factory & entry point
├── config.py           # Configuration settings & database URI
├── extensions.py       # Isolated Flask-SQLAlchemy and LoginManager instances
├── models.py           # Relational database models (User, StaffProfile, Trek, Booking)
├── seed.py             # Script to initialize database and seed initial Admin user
├── openapi.yaml        # API definition specification file
├── requirements.txt    # Python dependencies
├── static/
│   └── css/
│       └── style.css   # Custom CSS rules and color palettes
├── templates/
│   ├── base.html       # Master Jinja2 template layout
│   ├── index.html      # Public landing page
│   ├── admin/          # Admin templates (dashboard, manage staff, manage treks)
│   ├── auth/           # Authentication templates (login, register)
│   ├── staff/          # Staff dashboard templates
│   └── user/           # Trekker templates (dashboard, bookings, history, profile)
└── routes/
    ├── admin.py        # Admin controller blueprint
    ├── auth.py         # Authentication controller blueprint
    ├── staff.py        # Staff controller blueprint
    └── user.py         # User controller blueprint

    Setup & Running Instructions
1. Prerequisites
Ensure you have Python 3.8+ installed on your machine.

2. Set Up Virtual Environment (Recommended)
On Windows:

Bash
python -m venv venv
venv\Scripts\activate
On macOS / Linux:

Bash
python3 -m venv venv
source venv/bin/activate
3. Install Dependencies
Install all required packages using the provided requirements.txt:

Bash
pip install -r requirements.txt
4. Initialize Database & Seed Admin User
Run the seeding script to automatically create SQLite database tables (instance/trekking.db) and seed the default administrator account:

Bash
python seed.py
Output should display: Database initialized and Admin user created.

5. Run the Application
Start the Flask development server:

Bash
python app.py
The application will be accessible at: http://127.0.0.1:5000/

Default Credentials
Administrator Account
Email: admin@trekking.com
Password: admin123

Staff & User Accounts
Additional Trekker or Staff accounts can be created directly on the Register page (/auth/register).
