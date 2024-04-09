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
                sh 'mvn verify sonar:sonar -Dsonar.projectKey=Pet-Clinic -Dsonar.projectName='Pet Clinic' -Dsonar.host.url=http://localhost:9000 -Dsonar.token=sqp_175ff9749f07e5ec29e601cacb1b38d60f9cdb6e'
            }
        }
        stage('Run') {
            steps {
                sh './mvnw spring-boot:run'
            }
        }
    }
}
