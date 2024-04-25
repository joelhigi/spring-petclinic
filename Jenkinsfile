pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
        }
        stage('Ansible Deployment') {
            steps {
                sh 'ansible-playbook -i ansible_hosts.ini ansible_pb.yaml'
            }
        }
        stage('Deployment Successful'){
            steps{
                echo 'Pet Clinic deployed at http://localhost:8081.'
            }
        }
    }
    post {
        success {
            echo 'Pet Clinic build successful.'
        }
        failure {
            echo 'Pet Clinic failed to build.'
        }
    }
}
