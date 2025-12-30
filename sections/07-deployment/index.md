---
title: Deployment
has_children: false
nav_order: 8
---

# Deployment

### Download the project
Choose one of the following:
1. Option A — Download ZIP from GitHub
2. Option B — Clone with Git:
```
git clone https://github.com/unibo-dtm-se-2324-MedBook/medbook-application-core.git
cd medbook-application-core
```

### Install Dependencies
1. Poetry will create a virtual environment and install all required packages:
```
poetry install
```
2. Production-only install: no developer tools:
```
poetry install --only main 
```
### Environment Variables (Secrets)
To run the application end to end, you need:
* a Firebase project (create _Realtime Database, Authentication, and Storage_)
* configure the required secrets as environment variables, such as _Firebase admin key_, _Firebase key_, _Firebase service account_.

### Run the application
Use one of the options below:
1) Run by module
```
poetry run python artefact/__init__.py
```
2) Run via CLI command
```
poetry run medbook
```
### Run tests
A textual coverage summary is printed automatically when running the standard test task:
```
poetry run pytest
```
 To generate an HTML coverage report, use the next code line:
```
poetry run pytest --cov=artefact --cov-report=term-missing --cov-report=html
```
