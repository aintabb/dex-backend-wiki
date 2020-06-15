# SonarQube
This guide will show you how to run SonarQube for the DeX backend & frontend.

## Backend
### Prerequisites:
1. Docker is installed - Recommended: [Docker Desktop Overview](https://docs.docker.com/desktop/)
2. SonarQube is installed -  Recommended: [SonarQube - Get Started in Two Minutes Guide](https://docs.sonarqube.org/latest/setup/get-started-2-minutes/)
3. Java SDK is installed and accesible via the following command:
```bash
java -version
```
4. Dotnet Core SDK is installed and accesible via the following command:
```bash
dotnet --version
```

### Installation of SonarScanner
[Install SonarScanner for MSBuild](https://docs.sonarqube.org/latest/analysis/scan/sonarscanner-for-msbuild/)

I recommend the following method:
```bash
dotnet tool install --global dotnet-sonarscanner --version 4.8.0
```

### Run SonarScanner
1. Open your SonarQube instance and create a project named: `dex-backend`
2. Open terminal in root of project
3. Run the following commands
```bash
dotnet sonarscanner begin /k:dex-backend
dotnet build
dotnet sonarscanner end 
```
4. Navigate to your SonarQube panel (by default this is http://localhost:9000/)
5. See the results

## Frontend

### Prerequisites:
1. Docker is installed - Recommended: [Docker Desktop Overview](https://docs.docker.com/desktop/)
2. SonarQube is installed -  Recommended: [SonarQube - Get Started in Two Minutes Guide](https://docs.sonarqube.org/latest/setup/get-started-2-minutes/)

### Installation of SonarScanner
[Install SonarScanner](https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/)

### Run SonarScanner
1. Open your SonarQube instance and create a project named: `dex-frontend`
2. Open terminal in root of project
3. Run the following command
```bash
sonar-scanner
```
4. Navigate to your SonarQube panel (by default this is http://localhost:9000/)
5. See the results