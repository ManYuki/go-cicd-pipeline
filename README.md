# Go CI/CD Automation Pipeline

[![CI Pipeline](https://github.com/ManYuki/go-cicd-pipeline/actions/workflows/ci.yml/badge.svg)](https://github.com/ManYuki/go-cicd-pipeline/actions/workflows/ci.yml)
![Go Version](https://img.shields.io/badge/Go-1.21+-00ADD8?style=flat&logo=go)
![Runner](https://img.shields.io/badge/Runner-Ubuntu--Latest-E95420?style=flat&logo=ubuntu)
![Automation](https://img.shields.io/badge/Automation-GitHub_Actions-2088FF?style=flat&logo=github-actions)

A Continuous Integration (CI) pipeline designed to automatically test, build, and verify a Go application upon every code change. This project demonstrates foundational DevOps practices by embedding automation directly into the repository.

---

## Why This Matters

Building CI pipelines solves several common software development problems:

* **Catching Bugs Early:** By automatically running tests every time code is pushed, we catch errors before they merge into the main branch.
* **Consistent Environments:** Running the build on a fresh GitHub server (Ubuntu) prevents the classic "it works on my machine" problem.
* **Secure Configuration:** Using GitHub Secrets ensures that sensitive data (like database passwords) is passed securely during testing without being exposed in the code itself.
* **Fast Execution:** Caching downloaded dependencies speeds up the pipeline, meaning developers do not have to wait long to see if their code passes.

---

## Repository Structure

```text
.
├── .github/
│   └── workflows/
│       └── ci.yml          # The pipeline configuration
├── go.mod                  # Go dependency 
├── main.go                 # Main application code
├── main_test.go            # Automated tests
└── README.md               # Documentation
```

Local Development Guide

If you want to pull this code down and run it on your own machine, follow these steps.

Prerequisites:
Ensure you have Git and Go (v1.21+) installed on your local machine.


1. Clone the repository
Bash

git clone [https://github.com/ManYuki/go-cicd-pipeline.git](https://github.com/ManYuki/go-cicd-pipeline.git)
cd go-cicd-pipeline

2. Download dependencies
Bash

go mod download

3. Run the automated tests
Bash

go test -v ./...
