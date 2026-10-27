# Health Information System

## Objective
Develop a simple Django application to organize patient details, doctor information, appointment schedules and medical visit records for clinic staff.

## Problem statement
Paper records are difficult to search and update. This project provides a central database and a browser interface to reduce repetitive manual record handling.

## Modules
1. Authentication: staff sign in, sign out and admin-managed accounts.
2. Dashboard: record counts and today's appointments.
3. Patients: demographic and contact information.
4. Doctors: specialization and contact details.
5. Appointments: patient, doctor, scheduled time, reason and status.
6. Medical records: visit date, symptoms, diagnosis, prescription and notes.

## Architecture
Browser → Django URL routing → staff access check → view → ModelForm / ORM → SQLite.
Views pass data to HTML templates; CSS styles the rendered interface.
Django follows Model–View–Template (MVT).

## Database design
All models have an automatically generated integer primary key named id.
- Patient: name, date_of_birth, gender, phone, email, address, blood_group.
- Doctor: name, specialization, phone, email.
- Appointment: patient_id (FK), doctor_id (FK), scheduled_at, reason, status.
- MedicalRecord: patient_id (FK), doctor_id (FK), visit_date, symptoms, diagnosis, prescription, notes.
One patient and one doctor can each have many appointments and medical records.
Foreign keys use PROTECT to preserve linked history. Active appointment times have unique doctor/time and patient/time constraints.

## Algorithm
Start → staff login → dashboard → choose module → enter or search records → validate input → save in SQLite → display result → logout.

## Learning outcomes
Understand Django projects and apps, MVT, relational models, ORM queries, forms, validation, authentication, CSRF, templates, static files and migrations.

## Limitations and future scope
Local educational scope; no patient portal, billing, laboratory uploads, automatic clinical advice, audit trail or deployment setup. Future enhancements could add department roles, visit durations, appointment reminders, billing and backup management.

## Viva questions and answers
1. What is Django? A Python framework for building web applications.
2. What is MVT? Model manages data, View processes requests, Template displays the page.
3. Which database is used? SQLite, a file-based relational database.
4. What is ORM? It allows database operations using Python model objects.
5. What is a migration? A versioned description of database schema changes.
6. What is a foreign key? A field linking one table to another table's record.
7. Why use ModelForm? It generates and validates a form from a model definition.
8. What is CSRF protection? A token check that helps prevent unauthorized cross-site form submissions.
9. How are passwords stored? Django stores password hashes rather than plaintext passwords.
10. Why protect related records? To avoid deleting a patient or doctor while linked visit history exists.
11. Why use POST for deletion? Deleting changes data; GET requests only display confirmation.
12. What is a superuser? An administrator with full Django admin permissions.
