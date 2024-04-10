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
                    sh 'mvn verify sonar:sonar'
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
