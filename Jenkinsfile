/* groovylint-disable LineLength */
pipeline {
    agent {
        label '1c-node'
    }
    environment {
        envString = 'world'
    }

    post {
        always {
             allure commandline: 'Allure 2.41.0', includeProperties: false, jdk: '', resultPolicy: 'LEAVE_AS_IS', results: [[path: 'out/syntax-check/allure']]
        }
        failure {
            bat 'echo failure'
        }
        success {
            bat 'echo succes'
        }
    }
    stages {
        stage('Git Sync') {
            steps {
                bat 'chcp 65001\n gitsync --v8version 8.3.27.1606 sync --storage-user gs_bot C:\\хранилища\\хранилище1 C:\\repo\\jenkins-2025-12\\src'
            }
        }
        stage('Build test base') {
            steps {
                bat 'chcp 65001\n vrunner init-dev --v8version 8.3.27.1606 --ibconnection /FC:\\repo\\jenkins-2025-12\\build\\ib --dt C:\\jenkins\\template\\1Cv8.dt --src C:\\repo\\jenkins-2025-12\\src'
            }
        }
        stage('Syntax check') {
            steps {
                bat 'chcp 65001\n cd C:\\repo\\jenkins-2025-12 \n vrunner syntax-check'
            }
        }
        stage('Xunit tests') {
            steps {
                bat 'chcp 65001\n cd C:\\repo\\jenkins-2025-12 \n vrunner xunit'
            }
        }
    }
}

