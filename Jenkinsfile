pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh './mvnw clean package'
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
        stage('SonarQube Analysis') {
            steps{
                def mvn = tool 'Maven';
                withSonarQubeEnv('SonarQube') {
                    sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=Pet-Clinic -Dsonar.projectName='Pet Clinic'"
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
