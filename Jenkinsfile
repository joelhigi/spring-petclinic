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
                script {
                    def mvn = tool 'Maven';
                    withSonarQubeEnv('SonarQube') {
                        sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=Pet-Clinic -Dsonar.projectName='Pet Clinic'"
                    }
                }
            }
        }
        stage('Run') {
            steps {
                sh './mvnw spring-boot:run'
            }
        }
    }
}
