# SonarQube

## StartUp SonarQube Server
```sh
docker compose up -d
```
## Install SDKMAN
```sh
curl -s "https://get.sdkman.io" | bash
source "$HOME/.sdkman/bin/sdkman-init.sh"
```
## Install Java
```sh
sdk install java
```

## Install Spring Boot CLI
```sh
sdk install springboot
spring --version
```

## Spring Boot Project
```sh
spring init --dependencies=web --java-version=21 --language=java my-demo-app
```
