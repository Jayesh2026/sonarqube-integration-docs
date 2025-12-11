# SonarQube Setup for Angular Project

This file explains how to integrate SonarQube with an Angular project using TypeScript and Karma.

---

## 1. Install SonarScanner

Install globally:

```bash
npm install -g sonarqube-scanner
```

Alternatively (local install):

```bash
npm install sonarqube-scanner --save-dev
```

---

## 2. Install Coverage Tool

Angular uses Karma + Istanbul for coverage.

Install:

```bash
npm install --save-dev karma-coverage
```

---

## 3. Generate Test Coverage

Run:

```bash
ng test --watch=false --code-coverage
```

This produces:

```file
coverage/lcov.info
```

SonarQube reads this file to calculate coverage.

---

## 4. Create `sonar-project.properties`

Place this file in the Angular project root:

```properties
sonar.projectKey=your-angular-key
sonar.projectName=Your Angular Project
sonar.host.url=http://localhost:9001
sonar.token=YOUR_TOKEN

# Sources
sonar.sources=src
sonar.sourceEncoding=UTF-8

# Tests
sonar.tests=src
sonar.test.inclusions=**/*.spec.ts

# Exclusions
sonar.exclusions=**/*.spec.ts, **/node_modules/**, **/dist/**, **/e2e/**

# Coverage
sonar.javascript.lcov.reportPaths=coverage/lcov.info
sonar.typescript.lcov.reportPaths=coverage/lcov.info
```

---

## 5. Run Sonar Scan

```bash
sonar-scanner
```

---

## 6. Troubleshooting

### Error: "lcov.info not found"

Run tests again:

```bash
ng test --watch=false --code-coverage
```

### Error: "Unauthorized"

Regenerate token in SonarQube.

---

This completes full Angular + SonarQube setup.
