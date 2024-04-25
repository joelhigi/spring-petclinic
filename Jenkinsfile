pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh './mvnw clean package'
            }
        }
        stage('Clear ssh keys') {
            steps {
                sh 'ssh-keygen -f /var/lib/jenkins/.ssh/known_hosts -R "192.168.50.10"'
            }
        }
        stage('Ansible Deployment') {
            steps {
                sh 'ansible-playbook -i ansible_hosts.ini ansible_pb.yaml'
            }
        }
    }
}
