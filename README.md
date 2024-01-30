# React NodeJS Project

This repository contains a React NodeJS project with GitHub Actions workflows for linting, testing, building, deploying, and reporting.

## <u> Workflow: Website Deployment </u>
```yaml
.github/workflows/execution-flow.yml
```

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





## <u> Workflow: Matrix Demo </u>
```yaml
.github/workflows/matrix.yml
```
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






## <u> Workflow: Reusable Deploy </u> ```yaml .github/workflows/use-reusable.yml ```
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




## <u> Workflow: Continue Website Deployment </u>
```yaml
.github/workflows/continue.yml
```
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
  - Display information in case of failure
