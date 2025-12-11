# SonarQube Setup Toolkit

This repository provides a comprehensive toolkit for setting up and integrating SonarQube into your development workflow. It includes Docker Compose configurations for running a local SonarQube instance and detailed documentation for integrating SonarQube with popular frameworks and build tools.

## Features

- **Docker Compose Setup**: Easily spin up a SonarQube server with PostgreSQL database using Docker Compose.
- **Framework Integration Guides**: Step-by-step instructions for integrating SonarQube with:
  - Spring Boot (Gradle)
  - Spring Boot (Maven)
  - Angular
  - React
- **Code Quality Analysis**: Ensure code quality, maintainability, test coverage, security, and bug detection.
- **Production-Ready Configurations**: Includes test coverage setup and troubleshooting tips.

## Prerequisites

- Docker and Docker Compose installed on your system.
- JDK 17+ for Java-based projects (required for SonarQube 2025.x).
- Node.js and npm for JavaScript/TypeScript projects.

### For Windows WSL Users

Before starting SonarQube, you need to configure the virtual memory settings:

1. **Login to Docker Desktop WSL**:
   ```powershell
   wsl -d docker-desktop
   ```

2. **Set vm.max_map_count**:
   ```bash
   sysctl -w vm.max_map_count=262144
   ```

These commands ensure that Elasticsearch (used by SonarQube) has sufficient virtual memory to run properly.

## Quick Start

1. **Clone the repository**:
   ```bash
   git clone https://github.com/Jayesh2026/sonarqube-integration-docs.git
   cd SonarQube
   ```

2. **Start SonarQube Server**:
   ```bash
   docker compose -f docker/docker-compose-sonar.yml up -d
   ```

3. **Access SonarQube**:
   - Open your browser and go to `http://localhost:9001`
   - Default credentials: `admin` / `admin` (change on first login)

4. **Stop SonarQube**:
   ```bash
   docker compose -f docker/docker-compose-sonar.yml down
   ```

## Documentation

Detailed integration guides are available in the `docs/sonarqube-setup/` directory:

- [General SonarQube Integration](docs/sonarqube-setup/README.md)
- [Spring Boot with Gradle](docs/sonarqube-setup/gradle-setup.md)
- [Spring Boot with Maven](docs/sonarqube-setup/maven-setup.md)
- [Angular Integration](docs/sonarqube-setup/angular-setup.md)
- [React Integration](docs/sonarqube-setup/react-setup.md)

## Project Structure

```
SonarQube/
├── README.md                    # This file
├── docker/
│   └── docker-compose-sonar.yml # Docker Compose for SonarQube
└── docs/
    └── sonarqube-setup/
        ├── README.md            # General integration guide
        ├── gradle-setup.md      # Gradle setup
        ├── maven-setup.md       # Maven setup
        ├── angular-setup.md     # Angular setup
        └── react-setup.md       # React setup
```

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests for improvements, additional framework integrations, or bug fixes.

## Resources

- [SonarQube Official Documentation](https://docs.sonarqube.org/)
- [SonarQube Community](https://community.sonarsource.com/)
- [SonarScanner CLI Documentation](https://docs.sonarqube.org/latest/analyzing-source-code/scanners/sonarscanner/)
