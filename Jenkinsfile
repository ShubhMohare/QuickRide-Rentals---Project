pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/ShubhMohare/QuickRide-Rentals---Project.git'
            }
        }

        stage('SonarQube Scan') {
            steps {
                withSonarQubeEnv('sonarqube') {
                    sh '''
                    sonar-scanner \
                    -Dsonar.projectKey=QuickRide \
                    -Dsonar.sources=. \
                    -Dsonar.host.url=http://SONAR-IP:9000 \
                    -Dsonar.login=YOUR_TOKEN
                    '''
                }
            }
        }

        stage('Run Ansible') {
            steps {
                sh 'ansible-playbook ansible/deploy.yml -i ansible/inventory'
            }
        }
    }
}