pipeline {
    agent any

    stages {

        stage('clone') {
            steps {
                git branch: 'main',
                credentialsId: 'github-credentialsId',
                url: 'https://github.com/ShubhMohare/QuickRide-Rentals---Project.git'
            }
        }

        stage('build docker image') {
            steps {
                sh 'docker build -t quickride-rentals .'
            }
        }

        stage('run container') {
            steps {
                sh 'docker stop quickride-rentals || true'
                sh 'docker rm quickride-rentals || true'
                sh 'docker run -d -p 80:80 --name quickride-rentals quickride-rentals'
            }
        }
    }
}