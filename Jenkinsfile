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
                always {
                    mail to: "${env.STAGE_EMAIL}",
                         subject: "Hello1 and Integration Tests Stage Status: ${currentBuild.currentResult}",
                         body: "The Unit and Integration Tests stage has completed with status: ${currentBuild.currentResult}"
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality...'
                echo 'SonarQube'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                echo 'OWASP'
            }
            post {
               always {
                    mail to: "${env.STAGE_EMAIL}",
                         subject: "Hello2 Scan Stage Status: ${currentBuild.currentResult}",
                         body: "The Security Scan stage has completed with status: ${currentBuild.currentResult}"
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
               always {
                    mail to: "${env.STAGE_EMAIL}",
                         subject: "Hello3 Scan Stage Status: ${currentBuild.currentResult}",
                         body: "The Staging Scan stage has completed with status: ${currentBuild.currentResult}"
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
