pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/ShubhMohare/QuickRide-Rentals---Project.git'
            }
        }

        stage('Run Ansible') {
            steps {
                sh 'ansible-playbook ansible/deploy.yml -i ansible/inventory'
            }
        }

    }
}
