# SonarQube Setup for Maven Project

This document provides a complete guide to integrating SonarQube into Maven-based Spring Boot projects.

---

## 1. Add Sonar Properties in `pom.xml`

Inside `<properties>`:

```xml
<properties>
    <sonar.projectKey>your-project-key</sonar.projectKey>
    <sonar.host.url>http://localhost:9001</sonar.host.url>
</properties>
```

SonarScanner is built into Maven, so no plugin installation is required.

---

## 2. Add Test Coverage (JaCoCo)

Add this plugin:

```xml
<build>
    <plugins>
        <plugin>
            <groupId>org.jacoco</groupId>
            <artifactId>jacoco-maven-plugin</artifactId>
            <version>0.8.12</version>

            <executions>
                <execution>
                    <goals>
                        <goal>prepare-agent</goal>
                    </goals>
                </execution>

                <execution>
                    <id>report</id>
                    <phase>verify</phase>
                    <goals>
                        <goal>report</goal>
                    </goals>
                </execution>
            </executions>
        </plugin>
    </plugins>
</build>
```

---

## 3. Run Sonar Scan

### Basic scan

```bash
mvn clean verify sonar:sonar -Dsonar.token=YOUR_TOKEN
```

### Full scan with coverage

```bash
mvn clean test verify sonar:sonar -Dsonar.token=YOUR_TOKEN
```

---

## 4. Troubleshooting

### Issue: "Unauthorized"

Ensure your token is correct.

### Issue: "Coverage not shown"

Ensure this file exists:

```file
target/site/jacoco/jacoco.xml
```

---

This completes SonarQube integration for Maven projects.
