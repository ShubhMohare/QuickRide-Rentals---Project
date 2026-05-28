stage('SonarQube Scan') {
    steps {
        script {
            def scannerHome = tool 'sonar-scanner'

            withSonarQubeEnv('sonarqube') {
                sh """
                ${scannerHome}/bin/sonar-scanner \
                -Dsonar.projectKey=QuickRide \
                -Dsonar.sources=. \
                -Dsonar.host.url=http://YOUR-SONAR-IP:9000 \
                -Dsonar.login=YOUR_TOKEN
                """
            }
        }
    }
}