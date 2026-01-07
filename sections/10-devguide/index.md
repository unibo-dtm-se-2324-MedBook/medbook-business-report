---
title: Developer guide
has_children: false
nav_order: 11
---

# Developer Guide

MedBook is an **open-source, non-commercial** project released under the CC BY-NC 4.0 license.
Welcome contributions from developers who are interested in improving the application, fixing bugs, or extending its functionality for non-commercial purposes.

To contribute to the project, please follow the steps below:
* Fork the repository on GitHub;
* Create a new branch for your changes;
* Implement your changes or new features in the codebase;
* Add or update unit tests relevant to your changes;
* Follow the Conventional Commits specification when writing commit messages;
* Open a Pull Request, clearly describing:
    * the changes you introduced,
    * the design decisions you made,
    * the motivation behind them.
* Once a pull request is submitted, the continuous integration pipeline will automatically verify:
    * code style and conventions,
    * test presence and correctness,
    * overall project consistency.

If all checks pass, the pull request can be reviewed and merged, resulting in an updated version of the software.

## Requirements

To build and run MedBook locally, the following environment is required:

**Runtime Environment**

```
Python >= 3.12, < 4.0
Poetry >= 2.0.0, < 3.0.0
```
**Application Dependencies**

```
flet==0.25.2
pyrebase4==4.8.0
firebase-admin==6.6.0
setuptools>=80.9.0,<81.0.0
```
**Development Dependencies**

```
pytest>=8.1.0
coverage>=7.4.0
pytest-cov>=7.0.0
```

All dependencies are managed via Poetry and defined in `pyproject.toml`.

## Configuring Firebase

MedHub relies on Firebase as its backend infrastructure for authentication, data storage, and file management.

### Firebase Components Used:
* **Firebase Realtime Database** is used to store and synchronize application data in real time, including medication schedules and user-related information;
* **Firebase Authentication** handles user registration, login, and session management;
* **Firebase Storage** is used for storing medical documents such as PDF files and medical images.

### Required Setup

To run the application end-to-end, you must:
1. Create a Firebase project.
2. Enable and configure:
    * Realtime Database;
    * Authentication;
    * Storage.
3. Configure the required secrets as environment variables, including:
    * Firebase Admin SDK private key;
    * Firebase API key;
    * Firebase service account credentials.

These credentials are required for secure access to Firebase services during application runtime.

## OpenFDA API Integration

MedHub integrates with the **OpenFDA Drugs@FDA API** to provide medication risk analysis and drug-related information.

Drugs@FDA includes most FDA-approved drug products since 1939. The majority of patient information, labels, approval letters, reviews, and regulatory data are available for drugs approved since 1998.

**Key Facts:**
* Data Source: Drugs@FDA
* Data Format: JSON (converted and normalized by openFDA)
* Time Period Covered: from 1939 – nowadays
* Update Frequency: Daily (Monday–Friday)

**The openFDA API is used to:**
* retrieve drug-related metadata;
* analyze potential risks based on user biological attributes (e.g., age, sex, region);
* support the medication risk check feature inside the application.