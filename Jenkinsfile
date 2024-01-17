pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: main, url = 'https://github.com/alannewton/lbg-vat-calculator.git'
            }
        }
        stage('SonarQube Analysis') {
            environment {
                scannerHome = tool 'sonarqube'
            }

            steps {
                withSonarQubeEnv('sonarqube-an') {
                    sh "${scannerHome}/bin/sonar-scanner"
                }
            }
        }
    }
}