pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
        }
        stage('SonarQube Analysis') {
            steps{
                script{
                    sh 'mvn clean verify sonar:sonar -Dsonar.login=admin -Dsonar.password=sonarpass -Dsonar.projectKey=Pet-Clinic -Dsonar.projectName='Pet Clinic' -Dsonar.host.url=http://localhost:9000 -Dsonar.token=sqp_175ff9749f07e5ec29e601cacb1b38d60f9cdb6e'
                }
            }
        }
        stage('Run') {
            steps {
                sh 'java -jar target/spring-petclinic-3.2.0-SNAPSHOT.jar --server.port=8081'
            }
        }
    }
}
