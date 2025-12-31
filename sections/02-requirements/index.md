---
title: Requirements
has_children: false
nav_order: 3
---

# Requirements

## Functional Requirements

* User Authentication and Account Access: users must be able to register and authenticate securely using their email address and password via Firebase Authentication.
    * Acceptance Criteria: 
        * Successful authentication grants access to the user’s personal medical data and application features;
        * Authentication sessions must persist securely across application restarts.
* Medication Schedule Management: users should be able to create, view, edit, and delete medication entries associated with specific dates in a monthly calendar view.
    * Acceptance Criteria: 
        * Medication data must be stored and synchronized using Firebase Realtime Database;
        * Selecting a calendar date displays all medications scheduled for that day, including dosage and notes.
* Daily Medication Reminder: the application should notify users daily to remind them to take their medications.
    * Acceptance Criteria:
        * Notifications must be triggered automatically at a predefined time (6:00 AM);
        * Reminder logic must be implemented via an asynchronous background process.
* Medical Document Management: users should be able to upload, download, and delete personal medical documents (PDF files and images).
    * Acceptance Criteria:
        * Documents must be securely stored in Firebase Storage;
        * Uploaded files must remain accessible across user sessions and devices.
* Medication Risk Assessment: users should be able to analyze potential medication risks based on biological parameters such as age, sex, and country of origin.
    * Acceptance Criteria:
        * Risk analysis must be performed using data retrieved from the OpenFDA API;
        * Results should be visualized using charts to improve interpretability.
* Profile Management: users must be able to update personal profile information, including name and email address.
    * Acceptance Criteria:
        * Changes must be persisted immediately in Firebase Authentication and reflected in the UI without requiring a new login.

## Non-Functional Requirements

* Security: all user data must be protected during transmission and storage.
    * Acceptance Criteria:
        * Firebase security rules must restrict unauthorized access;
        * Sensitive credentials must be stored as environment variables.
* Usability: the application should provide an intuitive and accessible user interface suitable for non-technical users.
    * Acceptance Criteria:
        * Navigation between pages should be clear and consistent;
        * User actions must provide immediate visual feedback.
* Performance: the application should respond promptly to user interactions.
    * Acceptance Criteria:
        * Page transitions and database operations should complete within acceptable time limits.
* Availability: the system should be available continuously, except for planned maintenance.
    * Acceptance Criteria:
        * Firebase-hosted services must ensure high availability and data persistence.

## Implementation Requirements

* Backend Services: backend logic must rely on managed cloud services rather than a custom server.
    * Acceptance Criteria:
        * Firebase Realtime Database must be used for structured data storage;
        * Firebase Authentication must manage user sessions and identities.
* Frontend Application: the application must be implemented as a mobile UI using the Flet framework.
    * Acceptance Criteria:
        * UI components must be responsive and adapt to different screen sizes.
        * All interactions must follow a consistent design system defined in shared style modules.
* Third-Party API Integration: the system must integrate external medical data sources for risk assessment.
    * Acceptance Criteria:
        * Integration with the OpenFDA API must follow REST principles.
        * API responses must be validated and handled gracefully in case of missing or incomplete data.