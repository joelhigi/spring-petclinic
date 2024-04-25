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
