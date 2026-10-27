# Health Information System using Django

An MCA mini project for managing a small clinic. Stack: Python, Django 5.2, HTML, CSS and SQLite. No external database or CSS service is needed. Use Python 3.12 or 3.13 for a straightforward setup.

## Run in Windows / VS Code
1. Extract the ZIP. Open the Health_Information_System folder in VS Code.
2. Open Terminal → New Terminal. Ensure this folder contains manage.py.
3. Run these commands in PowerShell (activation is not needed):

```powershell
py -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe manage.py migrate
.\.venv\Scripts\python.exe manage.py createsuperuser
.\.venv\Scripts\python.exe manage.py runserver
```

Enter a username, optional email and your own password during createsuperuser. The password is hidden while typing. No default login is shipped.
Open http://127.0.0.1:8000/ and sign in. Admin: http://127.0.0.1:8000/admin/ . Stop the server with Ctrl+C.
If `py` is unavailable, use `python` in the first command after installing Python and enabling Add Python to PATH.

## Linux / macOS
```bash
python3 -m venv .venv
.venv/bin/python -m pip install -r requirements.txt
.venv/bin/python manage.py migrate
.venv/bin/python manage.py createsuperuser
.venv/bin/python manage.py runserver
```

## Demonstration workflow
1. Add a doctor with a specialization.
2. Add a patient with date of birth and contact details.
3. Add an appointment by selecting the patient and doctor.
4. Update its status to Completed after the visit.
5. Add a medical record with symptoms, diagnosis and prescription.
6. Search lists and use Edit or Delete. A confirmation page protects deletion.
7. The dashboard displays totals and today's appointments in India time.

Every application page requires an active staff account. A superuser can create additional users in Admin → Users and enable Staff status for clinic access. Non-staff users have no clinic access. All clinic staff can access all clinic records; this project does not implement departmental or patient-specific permissions.

## Features and validation
- Staff sign in / POST sign out and Django admin.
- Add, list, search, edit and delete patients, doctors, appointments and medical records.
- Pagination, responsive interface, dashboard and empty states.
- Foreign keys protect patient/doctor history from accidental cascading deletion.
- Future birth dates are rejected.
- Exact matching appointment times cannot be booked twice for a doctor or patient unless cancelled. Appointment duration/overlapping intervals are not modeled.
- Server-side forms, CSRF protection and escaped templates.

## Project structure
- health_system/: settings, main URLs, WSGI entry point.
- records/: models, forms, views, routes, admin, migrations and tests.
- templates/: dashboard, lists, forms, login and confirmation pages.
- static/style.css: responsive design.
- PROJECT_REPORT.md: objective, architecture, tables, scope and viva questions.

## Tests
```powershell
.\.venv\Scripts\python.exe manage.py test
.\.venv\Scripts\python.exe manage.py check
```
The database is created locally by migrate. No patient data or credentials are included.
This is an educational local application. Before using real patient information, production work is required for deployment settings, HTTPS, secrets, access policies, audit history, backups, encryption and applicable privacy requirements. The development server is for local testing only.

Reference: https://docs.djangoproject.com/en/5.2/topics/install/
