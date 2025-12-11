# SonarQube Setup for Spring Boot (Gradle)

This guide provides a complete and production-ready SonarQube integration for applications built using Gradle.

---

## 1. Add SonarQube Plugin

Add this plugin to `build.gradle`:

```gradle
plugins {
    id "org.sonarqube" version "7.0.1.6134"
}
```

This plugin enables SonarQube scanning through Gradle tasks.

---

## 2. Configure Sonar Properties

Add this block inside `build.gradle`:

```gradle
sonar {
    properties {
        property "sonar.projectKey", "your-project-key"
        property "sonar.projectName", "Your Project Name"
        property "sonar.host.url", "http://localhost:9001"
        property "sonar.token", "YOUR_TOKEN"
        property "sonar.gradle.skipCompile", "true"
    }
}
```

### Explanation

| Property | Purpose |
|----------|---------|
| `sonar.projectKey` | Unique ID inside SonarQube |
| `sonar.projectName` | Human readable name |
| `sonar.token` | Authentication token from SonarQube |
| `sonar.gradle.skipCompile` | Improves performance (Gradle already compiles code) |

---

## 3. Add Test Coverage (Recommended)

Install JaCoCo:

```gradle
apply plugin: 'jacoco'

jacocoTestReport {
    dependsOn test
    reports {
        xml.required = true
        html.required = true
    }
}
```

---

## 4. Run SonarQube Scan

### Basic scan

```bash
./gradlew sonar
```

### Including coverage

```bash
./gradlew clean test jacocoTestReport sonar
```

---

## 5. Troubleshooting

### Issue: "Token not found"

Regenerate token in:
**SonarQube → My Account → Security → Generate token**

### Issue: Scan fails due to Java version

Ensure JDK 17+ is used (SonarQube 2025.x requirement).

### Issue: Server unreachable

Verify connection:

```bash
curl http://localhost:9001/api/system/status
```

---

This completes SonarQube integration for Gradle projects.
