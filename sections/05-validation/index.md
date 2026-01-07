---
title: Validation
has_children: false
nav_order: 6
---

# Validation

## Testing

This section describes the testing strategy adopted for the MedBook application, including the testing process, success rate, coverage, and compliance with the defined requirements and acceptance criteria.

### Testing Process

We adopted a **unit-first approach** focused on UI components and page logic, using pytest (+ `pytest-cov`) and extensive **mocking** of external services. Real network (Firebase, openFDA, Storage) is not exercised in unit tests; instead, calls are patched and their effects are asserted at the UI-layer.

Key practices:
* Tests are written after feature implementation, and are refactored when the UI or flow changes.
* UI controls are tested through <u>page stubs</u> (fake `Page`, `Session`, etc.), and Flet updates are neutralized where needed to keep tests hermetic.
* External deps are <u>monkeypatched</u> (`firebase_admin`, `documents_page_service`, `api_openfda_service`, etc.) to verify that the correct calls are made and the UI reacts properly.

### Coverage

The test coverage of the MedBook application is **approximately 82%** of the total codebase:

<img src="../../pictures/tests.png"/>

* UI pages / components: ~96–100% each;
* Service / integration modules: ~30–45% (mocked at call sites; no network in unit scope);
* A detailed HTML report is generated on demand; the CLI table is produced on each run.

### Comments w.r.t. Requirements’ Acceptance Criteria

Automated unit tests validate the visible, user-facing behavior for:
* Authentication flows (routing, token handling, validation feedback);
* Schedule logic (month navigation, per-day dialogs, add/delete items);
* Documents UI (grid population, action wiring, error handling);
* Risk analysis UI (input validation, API result rendering, chart, error/exception handling).

Where acceptance criteria rely on external systems (Firebase, openFDA, Storage), unit tests assert that **the correct calls would be made** and that **the UI responds correctly** to success/error signals. End-to-end verification of those systems is left to future integration/e2e tests.

## Acceptance Testing

Manual acceptance testing covered the full user journeys:
1. **Registration**: redirect from First page for unknown email; account creation flow visible in UI;
2. **Login**: existing email path; successful flow navigates to the main page; invalid password shows error;
3. **Medication Schedule**: month switch, day dialog, add/delete entries reflected in the calendar;
4. **Daily Reminders**: notification bootstrap verifies single initialization at first build (UI evidence);
5. **Documents**: UI displays empty and non-empty states; actions wired to upload/download/delete;
6. **Medication Risk Check** form validation, 'Search for risks' result rendering and error/exception feedback;
7. **Profile Settings**: load current info (mocked), edit dialog, save with validation and UI updates.

All scenarios passed at the time of testing.

### Next steps to raise coverage
* Add integration tests for `authentication`, `database`, `documents_page_service`, `notifications`, and `api_openfda_service` against test backends/mocks at HTTP layer;
* Expand unit tests for `utils/validation` to cover edge cases and negative branches;
* Consider a lightweight e2e smoke suite for the highest-risk flows (login, add pill, upload document).