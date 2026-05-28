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
                script {
                    def scannerHome = tool 'sonar-scanner'

                    withSonarQubeEnv('sonarqube') {
                        sh """
                        ${scannerHome}/bin/sonar-scanner \
                        -Dsonar.projectKey=QuickRide \
                        -Dsonar.sources=. \
                        -Dsonar.host.url=http://13.201.29.165:9000 \
                        -Dsonar.login=squ_8df336caa5c0aea316f6f68b7234ce82c9d543df
                        """
                    }
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