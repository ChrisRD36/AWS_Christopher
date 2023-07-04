# Instrucciones para Aplicacion Angular

### Agente 
El agente para ejecutar la app Dotnet tiene por etiqueta `linux-agent`

### Comandos a Ejecutar

| Fase | Comando |
| ------ | ------ |
| Dependencies | **npm install** |
| SonarScanner | **Revisar Seccion de SonarQube** |
| Build | **npm run build** |
| Deploy | **Revisar el documento donde tienen la informacion de Deployment** |

### SonarQube

```sh
stage('Run SonarQube'){
    steps{
        withSonarQubeEnv('SonarQubeCursoCI') {
            sh "/opt/sonar-scanner/bin/sonar-scanner -Dsonar.projectKey=AngularApp"
        }
    }
}
```