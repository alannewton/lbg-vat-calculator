pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/alannewton/lbg-vat-calculator.git'
            }
        }
        stage('SonarQube Analysis') {
            environment {
                scannerHome = tool 'sonarqube'
            }

            steps {
                withSonarQubeEnv('sonarqube-alan') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
                
                timeout(time: 10, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}