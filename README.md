# React NodeJS Project

- [Workflow: Website Deployment](#workflow-website-deployment)
  - [Description](#description)
  - [Jobs](#jobs)
    - [1. Lint](#1-lint)
    - [2. Test](#2-test)
    - [3. Build](#3-build)
    - [4. Deploy](#4-deploy)
    - [5. Report](#5-report)

- [Workflow: Matrix Demo](#workflow-matrix-demo)
  - [Description](#description-1)
  - [Jobs](#jobs-1)
    - [1. Build](#1-build)

- [Workflow: Reusable Deploy](#workflow-reusable-deploy)
  - [Description](#description-2)
  - [Jobs](#jobs-2)
    - [1. Deploy](#1-deploy)

- [Workflow: Using Reusable Workflow](#workflow-using-reusable-workflow)
  - [Description](#description-3)
  - [Jobs](#jobs-3)
    - [1. Lint](#1-lint-1)
    - [2. Test](#2-test-1)
    - [3. Build](#3-build-1)
    - [4. Deploy](#4-deploy-1)
    - [5. Report](#5-report-1)

- [Workflow: Continue Website Deployment](#workflow-continue-website-deployment)
  - [Description](#description-4)
  - [Jobs](#jobs-4)
    - [1. Lint](#1-lint-2)
    - [2. Test](#2-test-2)
    - [3. Build](#3-build-2)
    - [4. Deploy](#4-deploy-2)
    - [5. Report](#5-report-2)

## Workflow: Website Deployment

### Description
This workflow runs on every push to the main branch. It consists of several jobs to lint the code, run tests, build the website, deploy the application, and generate a report in case of failures.

### Jobs:

#### 1. Lint
- **Runs On:** Ubuntu Latest
- **Steps:**
  - Get code
  - Cache dependencies
  - Install dependencies if cache miss
  - Lint code using npm run lint

#### 2. Test
- **Runs On:** Ubuntu Latest
- **Steps:**
  - Get code
  - Cache dependencies
  - Install dependencies if cache miss
  - Run tests using npm run test
  - Upload test report on failure

#### 3. Build
- **Runs On:** Ubuntu Latest
- **Dependencies:** Depends on the Test job
- **Steps:**
  - Get code
  - Cache dependencies
  - Install dependencies if cache miss
  - Build website using npm run build
  - Upload artifacts (dist folder)

#### 4. Deploy
- **Runs On:** Ubuntu Latest
- **Dependencies:** Depends on the Build job
- **Steps:**
  - Get build artifacts
  - Output contents (list files)
  - Deploy (echo "Deploying...")

#### 5. Report
- **Runs On:** Ubuntu Latest
- **Dependencies:** Depends on the Lint and Deploy jobs
- **Conditions:** Runs only on failure
- **Steps:**
  - Output information
  - Display information in case of failure

## Workflow: Matrix Demo

### Description
This workflow runs on push events and utilizes a matrix strategy to test the project on different Node.js versions and operating systems. It includes steps to get the code, install Node.js, install dependencies, and build the project.

### Jobs:

#### 1. Build
- **Continues On Error:** true
- **Runs On:** Matrix (Node.js versions and operating systems)
- **Steps:**
  - Get code
  - Install Node.js
  - Install dependencies
  - Build the project

## Workflow: Reusable Deploy

### Description
This workflow runs on workflow_call event and deploys the application by echoing "Deploying & uploading."

### Jobs:

#### 1. Deploy
- **Runs On:** Ubuntu Latest
- **Steps:**
  - Output information (echo "Deploying & uploading")

## Workflow: Using Reusable Workflow

### Description
This workflow runs on push events to the main branch. It consists of jobs to lint the code, run tests, build the website, deploy the application using the reusable workflow, and generate a report in case of failures.

### Jobs:

#### 1. Lint
- **Runs On:** Ubuntu Latest
- **Steps:**
  - Get code
  - Cache dependencies
  - Install dependencies if cache miss
  - Lint code using npm run lint

#### 2. Test
- **Runs On:** Ubuntu Latest
- **Steps:**
  - Get code
  - Cache dependencies
  - Install dependencies if cache miss
  - Run tests using npm run test
  - Upload test report on failure

#### 3. Build
- **Runs On:** Ubuntu Latest
- **Dependencies:** Depends on the Test job
- **Steps:**
  - Get code
  - Cache dependencies
  - Install dependencies if cache miss
  - Build website using npm run build
  - Upload artifacts (dist folder)

#### 4. Deploy
- **Depends On:** Build job
- **Uses:** Reusable Deploy workflow

#### 5. Report
- **Runs On:** Ubuntu Latest
- **Dependencies:** Depends on the Lint and Deploy jobs
- **Conditions:** Runs only on failure
- **Steps:**
  - Output information
  - Display information in case of failure

## Workflow: Continue Website Deployment

### Description
This workflow runs on push events to the main branch. It includes jobs to lint the code, run tests, build the website, deploy the application, and generate a report in case of failures.

### Jobs:

#### 1. Lint
- **Runs On:** Ubuntu Latest
- **Steps:**
  - Get code
  - Cache dependencies
  - Install dependencies if cache miss
  - Lint code using npm run lint

#### 2. Test
- **Runs On:** Ubuntu Latest
- **Steps:**
  - Get code
  - Cache dependencies
  - Install dependencies if cache miss
  - Run tests using npm run test
  - Upload test report on failure

#### 3. Build
- **Runs On:** Ubuntu Latest
- **Dependencies:** Depends on the Test job
- **Steps:**
  - Get code
  - Cache dependencies
  - Install dependencies if cache miss
  - Build website using npm run build
  - Upload artifacts (dist folder)

#### 4. Deploy
- **Runs On:** Ubuntu Latest
- **Dependencies:** Depends on the Build job
- **Steps:**
  - Get build artifacts
  - Output contents (list files)
  - Deploy (echo "Deploying...")

#### 5. Report
- **Runs On:** Ubuntu Latest
- **Dependencies:** Depends on the Lint and Deploy jobs
- **Conditions:** Runs only on failure
- **Steps:**
  - Output information
