pipeline {
    agent any

    environment {
        EMAIL_RECIPIENT = 'hashaamkhan542@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the code... using the command mvn clean package'
              
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests...'
                
            }
            post {
                always {
                    mail bcc: '', body: 'Unit and Integration Tests stage completed: ${currentBuild.currentResult}',
                        cc: '', from: '', replyTo: '', subject: "Jenkins Build: ${currentBuild.currentResult}",
                        to: "${env.EMAIL_RECIPIENT}"
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing the code using SonarQube...'
                
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running Security Scan using OWASP Dependency Check...'
                
            }
            post {
                always {
                    mail bcc: '', body: "Security Scan stage completed: ${currentBuild.currentResult}",
                        cc: '', from: '', replyTo: '', subject: "Jenkins Build: ${currentBuild.currentResult}",
                        to: "${env.EMAIL_RECIPIENT}"
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging using AWS...'
               
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running Integration Tests on Staging...'
              
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
           
            }
        }
        stage('Checking') {
            steps {
                echo 'Checking'
           
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished'
        }
    }
}
