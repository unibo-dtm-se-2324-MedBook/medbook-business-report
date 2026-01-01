---
title: Concept
has_children: false
nav_order: 2
---

# Concept

The project consists of developing MedBook, a personal medical management application designed to centralize and digitalize health-related information for individual users. The goal of the application is to support users in managing their medications, medical documents, and health risks in a structured, secure, and user-friendly way.

More specifically, the application is composed of the following main components:
* **Backend services**, responsible for user authentication, data persistence, and integration with external APIs (Firebase services and OpenFDA).
* **Frontend application**, implemented as a desktop application using the Flet framework, providing an interactive graphical user interface for end users.

## Use Case 1: User Registration and Authentication

* **Actors**: User, Firebase Authentication Service
* **Description**: Users can register and authenticate securely using their email address and password to access their personal medical data.
* **Main Flow**:
    * The user opens the MedBook application;
    * The user enters an email address;
    * If the email is already registered, the user is redirected to the login page;
    * If the email is not registered, the user is redirected to the sign-up page;
    * After successful authentication, the user gains access to the personal dashboard.

## Use Case 2: Managing Medication Schedule

* **Actors**: Authenticated User, Firebase Realtime Database
* **Description**: The user can create and manage a medication intake schedule using a monthly calendar view.
* **Main Flow**:
    * The user logs into the application;
    * The user is redirected to the medication calendar page;
    * The user can select a specific date, either he can add new medications by clicking the button;
    * If the user selects, he views the list of medications scheduled for that day;
    * The user can edit, or remove medications, including dosage and notes;
    * The system stores the information in the Firebase Realtime Database.

## Use Case 3: Daily Medication Reminder

* **Actors**: Authenticated User, Notification Service
* **Description**: The application provides automated daily reminders to notify users about their medication intake.
* **Main Flow**:
    * The system schedules a background task upon user login;
    * Every day at a predefined time (6:00), the reminder service is triggered asynchronously;
    * The user receives a notification reminding them to take their medication.

## Use Case 4: Medical Document Management

* **Actors**: Authenticated User, Firebase Storage
* **Description**: Users can upload, download, and manage medical documents such as reports, scans, and test results.
* **Main Flow**:
    * The user navigates to the Documents section;
    * The user uploads medical documents in PDF or image format;
    * The documents are securely stored in Firebase Storage;
    * The user can view, download, or delete previously uploaded documents.

## Use Case 5: Medication Risk Analysis

* **Actors**: Authenticated User, OpenFDA API
* **Description**: The user can analyze potential risks associated with a medication based on biological and demographic factors.
* **Main Flow**:
    * The user opens the Medication Risk Check page;
    * The user enters the medication name and personal data (age, gender, country);
    * The application sends a request to the OpenFDA API;
    * The system processes the response and displays a visual risk analysis (pie chart);
    * The user reviews potential side effects and risk indicators.

## Use Case 6: User Profile Management
* **Actors**: Authenticated User, Firebase Authentication Service
* **Description**: The user can view and update personal profile information, such as name, surname, and email address, directly from the application settings.
* **Main Flow**:
    * The user logs into the MedBook application;
    * The user navigates to the Settings section;
    * The application retrieves the current user profile data from Firebase Authentication;
    * The user selects the option to edit profile information;
    * The user modifies personal details (name, surname, email);
    * The updated information is validated on the client side;
    * The application updates the user profile using Firebase Authentication services;
    * The updated profile information is immediately reflected in the application interface.
* **Alternative Flow**:
    * If the provided data does not meet validation rules (invalid email format), the system displays an error message and prevents the update.