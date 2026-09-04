[![Build Status](https://github.com/picsouds/sonar-l10n-fr/actions/workflows/main.yml/badge.svg)](https://github.com/picsouds/sonar-l10n-fr/actions/workflows/main.yml)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=picsouds_sonar-l10n-fr&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=picsouds_sonar-l10n-fr)
[![Bugs](https://sonarcloud.io/api/project_badges/measure?project=picsouds_sonar-l10n-fr&metric=bugs)](https://sonarcloud.io/summary/new_code?id=picsouds_sonar-l10n-fr)
[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=picsouds_sonar-l10n-fr&metric=coverage)](https://sonarcloud.io/summary/new_code?id=picsouds_sonar-l10n-fr)

# French Pack for SonarQube

This is the plugin to translate [SonarQube](http://www.sonarqube.org/) web application in French (Sonarqube 8.9 / 9.9 / 2025.x)

Fork of [sonar-l10n-fr](https://github.com/ZoeThivet/sonar-l10n-fr) adapted with [sonar-l10n-zh](https://github.com/xuhuisheng/sonar-l10n-zh)

## Releases (compatibility)

* Version 1.0.x from Sonarqube 8.9.0.43852 and above
* Version 2.0.x from Sonarqube 9.9.1.69595 and above
  * Version 2.0.2 from Sonarqube 9.9.6.92038 (backward compatibility ok)
* Version 25.1.0 from SonarQube: 25.1.0.102122-community / 25.1.5-enterprise (and above)

## Build the plugin locally

Clone the repository and build the plugin JAR :
```sh
mvn -B clean verify
```

> [!CAUTION]
> **Build requirements:** Maven 3.9.0 or later and Java 17 or later.

## 🐳 Quick Start with Docker

A Docker Compose example is provided to run SonarQube 25.1 locally with this plugin (or others).

### Prerequisites
- Docker & Docker Compose installed
- docker-compose.yml
```yaml
services:
  sonarqube-25.1:
    image: sonarqube:25.1.0.102122-community
    command: -Dsonar.ce.javaOpts=-Xmx1192m -Dsonar.web.javaOpts=-Xmx1192m
    container_name: sonarqube25.1
    depends_on:
      - sonarqube_db_25.1
    ports:
      - "9001:9000"
    networks:
      - sonar-net
    environment:
      - SONAR_JDBC_URL=jdbc:postgresql://sonarqube_db_25.1:5432/sonar
      - SONAR_JDBC_USERNAME=sonar
      - SONAR_JDBC_PASSWORD=sonar
    volumes:
      - ./plugins:/opt/sonarqube/extensions/plugins
      - "/etc/timezone:/etc/timezone:ro"
      - "/etc/localtime:/etc/localtime:ro"
  sonarqube_db_25.1:
    image: postgres:12.8
    container_name: sonarqube_db_25.1
    ports:
      - "5433:5432"
    networks:
      - sonar-net
    environment:
      POSTGRES_USER: sonar
      POSTGRES_PASSWORD: sonar
      POSTGRES_DB: sonar
    volumes:
      - local_pgdata_sonarqube_db_25.1:/var/lib/postgresql/data

volumes:
  local_pgdata_sonarqube_db_25.1:
networks:
  sonar-net:
    external: false
```

### Usage

1. Download the plugin JAR from [Releases](https://github.com/picsouds/sonar-l10n-fr/releases)
or use the locally built JAR from the `target/` directory, ***then copy it into the `plugins/` folder.***
2. Start the container :
```bash
docker compose up -d
```

3. Access SonarQube at http://localhost:9001 (default credentials: `admin` / `admin`)

## License

GNU LGPL 3

:warning:️ **STILL IN PROGESS (The most important is translated) :warning:
