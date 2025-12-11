# SonarQube Integration Documentation

This documentation provides complete, production-ready instructions for integrating SonarQube with:

- Spring Boot (Gradle)
- Spring Boot (Maven)
- Angular
- React

---

## Folder Structure

```bash
docs/sonarqube/
│
├── README.md
├── gradle-setup.md
├── maven-setup.md
├── angular-setup.md
└── react-setup.md
```

---

## Purpose of This Documentation

SonarQube helps teams ensure:

- Code quality
- Maintainability
- Test coverage
- Security vulnerability detection
- Bug & code smell identification

Each file provides:

- Installation steps
- Required packages
- Scanner setup
- Coverage configuration
- Correct SonarQube command usage
- Troubleshooting notes

---

## Prerequisites

### SonarQube Server

You must have a running SonarQube server using:

```bash
http://localhost:9001
```

or your custom deployed instance.

**Supported database (latest versions):**  
PostgreSQL 14 / 15

---

## Using This Documentation

Choose the correct file based on your project type:

| Project Type | Documentation |
|--------------|---------------|
| Spring Boot + Gradle | `gradle-setup.md` |
| Spring Boot + Maven | `maven-setup.md` |
| Angular | `angular-setup.md` |
| React | `react-setup.md` |

---

## Next Steps

For help integrating SonarQube in CI/CD (GitHub Actions, GitLab CI, Jenkins), contact your DevOps team or extend this documentation.

---

## Quick Links

- [SonarQube Official Documentation](https://docs.sonarqube.org/)
- [SonarQube Community](https://community.sonarsource.com/)
- [SonarScanner CLI Documentation](https://docs.sonarqube.org/latest/analyzing-source-code/scanners/sonarscanner/)
