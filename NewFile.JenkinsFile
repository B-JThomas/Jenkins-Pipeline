pipeline {
    agent any

    environment {
        STAGE_EMAIL = 'bailey.jthomas2@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                echo 'Maven'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                echo 'JUnit'
            }
            post {
                success {
                    mail to: "${env.STAGE_EMAIL}",
                    subject: "Pipeline Execution Testing",
                    body: "Pipeline Test with result: Success. Please check the logs.",
                    attachLog: true
                }
                failure {
                    mail to: "${env.STAGE_EMAIL}",
                    subject: "Pipeline Execution Security",
                    body: "Pipeline Test with result: Failure. Please check the logs.",
                    attachLog: true
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality...'
                echo 'SonarQube'
            }
            post {
                always {
                    echo 'Code analysis complete'
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                echo 'OWASP'
            }
            post {
                success {
                    mail to: "${env.STAGE_EMAIL}",
                    subject: "Pipeline Execution Security",
                    body: "Pipeline Test with result: Success. Please check the logs.",
                    attachLog: true
                }
                failure {
                    mail to: "${env.STAGE_EMAIL}",
                    subject: "Pipeline Execution Security",
                    body: "Pipeline Test with result: Failure. Please check the logs.",
                    attachLog: true
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
                echo 'AWS'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                echo 'Cypress'
            }
            post {
                success {
                    echo 'Integration tests on staging passed'
                }
                failure {
                    echo 'Integration tests on staging failed'
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment...'
                echo 'Ansible'
            }
        }
    }
}
