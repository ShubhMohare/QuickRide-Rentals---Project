pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git https://github.com/ShubhMohare/QuickRide-Rentals---Project.git'
            }
        }

        stage('Run Ansible') {
            steps {
                sh 'ansible-playbook ansible/deploy.yml -i ansible/inventory'
            }
        }
    }
}