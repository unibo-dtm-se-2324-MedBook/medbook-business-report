---
title: CI / CD
has_children: false
nav_order: 9
---

# Continuous Integration and Continuous Deployment

To ensure code quality, reliability, and reproducibility of the development process, two automated CI/CD workflows were implemented using GitHub Actions.

## Continuous Integration

The first workflow is dedicated to CI and is automatically triggered on each push or pull request to the main development branch. This CI pipeline performs the following tasks:
* checks the correctness of the project configuration and syntax (poetry check);
* installs the project dependencies in a clean environment;
* executes the full test suite using PyTest;
* measures code coverage using pytest-cov and reports coverage results directly in the workflow logs.

The CI workflow guarantees that:
* the codebase remains syntactically valid;
* all tests pass before changes are merged;
* regressions are detected early in the development cycle;
* the project is always in a buildable and testable state.

This automation significantly reduces the risk of introducing errors and enforces a consistent quality standard across all contributions.

## Continuous Deployment

The second workflow implements CD and is responsible for building, releasing, and publishing the software. This workflow is automatically triggered when a version tag (e.g. v1.0.0) is pushed to the repository. It performs the following steps:
* builds the Python package using Poetry, generating distribution artifacts (.whl and .tar.gz);
* publishes the package to the official PyPI repository;
* creates a corresponding GitHub Release, attaching the generated artifacts and providing release metadata.

By automating the release and deployment process, this workflow ensures that:
* releases are reproducible and traceable;
* published packages always correspond to a specific, versioned state of the source code;
* manual deployment errors are eliminated;
* the release process is fast, consistent, and reliable.

Overall, the implemented CI/CD infrastructure provides a robust and professional DevOps foundation, aligning the project with modern software engineering standards