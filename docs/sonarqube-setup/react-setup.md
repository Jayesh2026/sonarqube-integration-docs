# SonarQube Setup for React Project

React typically uses Jest for unit testing and Istanbul for coverage. This documentation explains how to integrate SonarQube properly.

---

## 1. Install SonarScanner

```bash
npm install -g sonarqube-scanner
```

---

## 2. Enable Coverage in Jest

Add this to `package.json`:

```json
"jest": {
  "collectCoverage": true,
  "coverageReporters": ["lcov"]
}
```

Run coverage:

```bash
npm test -- --coverage
```

This generates:

```file
coverage/lcov.info
```

---

## 3. Create `sonar-project.properties`

```properties
sonar.projectKey=your-react-key
sonar.projectName=Your React Project
sonar.host.url=http://localhost:9001
sonar.token=YOUR_TOKEN

# Sources
sonar.sources=src
sonar.sourceEncoding=UTF-8

# Coverage
sonar.javascript.lcov.reportPaths=coverage/lcov.info

# Exclusions
sonar.exclusions=**/*.test.js, **/node_modules/**, **/build/**
```

---

## 4. Run Scanner

```bash
sonar-scanner
```

---

## 5. Troubleshooting

### Issue: No coverage shown

Ensure coverage folder exists.

### Issue: Cannot find Jest config

Try:

```bash
npm test -- --coverage --watchAll=false
```

---

This completes SonarQube setup for React.
