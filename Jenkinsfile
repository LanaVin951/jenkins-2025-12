pipeline
{
agent {
label '1C_agent'
    }
environment {
        envString = 'world'
post {
always {
            }
allure includeProperties: false, jdk: '', resultPolicy: 'LEAVE_AS_IS', r 
junit allowEmptyResults: true, testResults: 'out/smoke/junit/*.xml'
        }

failure {
bat "echo failure"
        }

success {
bat "echo succes"
        }

stages {
            stage("Syntax check") {
steps {
                }
            }
            stage("Smoke tests") {
steps {
script {
                        try {
                                bat "chcp 65001\n vrunner xunit"
                        }
                        catch (Exception Exc) {
                            currentBuild.result = 'UNSTABLE'
                        }
                    }
                }
            }
            stage("Vanessa") {
steps {
script {
                        try {
bat "chcp 65001\n vrunner vanessa"
                        }
                        catch (Exception Exc) {
                            currentBuild.result = 'UNSTABLE'
                        }
                    }
                }
            }
            stage("Sonar") {
steps {
script {
                        scannerHome = tool 'sonar-scanner'
                    }
                }
            }
        }
    }
}
