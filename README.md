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
├── go.mod                  # Go dependency tracker
├── main.go                 # Main application code
├── main_test.go            # Automated tests
└── README.md               # Documentation
```

---

## Local Development Guide

If you want to pull this code down and run it on your own machine, follow these steps. 

**Prerequisites:**
Ensure you have Git and Go (v1.21+) installed on your local machine.

**1. Clone the repository**
```bash
git clone https://github.com/ManYuki/go-cicd-pipeline.git
cd go-cicd-pipeline
```

**2. Download dependencies**
```bash
go mod download
```

**3. Run the automated tests**
```bash
go test -v ./...
```

**4. Build the application**
```bash
go build -v -o bin/myapp ./main.go
./bin/myapp
```

---

## Pipeline Workflow Breakdown

The pipeline defined in `ci.yml` runs automatically whenever someone pushes code or opens a pull request to the `main` branch. Here is exactly what the automated server is instructed to do:

1. **Checkout Code:** Copies the repository files onto the automated server so they can be tested.
2. **Setup Go:** Installs Go and enables caching to speed up future runs.
3. **Install Dependencies:** Downloads any external packages the code needs to run.
4. **Run Tests:** Executes the test files to ensure the application logic is sound. It securely pulls in environment variables needed for the tests.
5. **Build Application:** Compiles the code into a runnable program to prove the architecture is stable.

---

## Troubleshooting Guide 

If you are contributing to this project or setting up a similar pipeline, you may run into dependency resolution errors. 

**Common Error: `go: no modules specified`**

```text
Run go mod download
go: no modules specified (see 'go help mod download')
Error: Process completed with exit code 1.
```

**Cause & Solution:** 
This occurs if the pipeline tries to run `go mod download` but cannot find a `go.mod` file in the root directory. To resolve this, ensure you have initialized a Go module locally (`go mod init <module-name>`) and committed the `go.mod` file to the repository before pushing your workflow file.
