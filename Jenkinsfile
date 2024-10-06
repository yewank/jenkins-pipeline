pipeline {
    agent any
    environment {
        EMAIL_RECIPIENTS = 'yewankospelawattaa@gmail.com
@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                echo 'Tool: Maven'
                // Simulate build command and log generation
                bat 'echo "Building the code using Maven"'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests with JUnit and integration tests...'
                echo 'Tools: JUnit for unit tests, TestNG for integration tests'
                // Simulate test log creation
                bat 'echo "Running Unit and Integration Tests"'
            }
            post {
                success {
                    emailext (
                        subject: "Unit and Integration Tests SUCCESS: Jenkins Job ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                        body: "Unit and integration tests passed successfully.",
                        to: "${env.EMAIL_RECIPIENTS}",
                        attachLog: true // Attach Jenkins build log
                    )
                }
                failure {
                    emailext (
                        subject: "Unit and Integration Tests FAILURE: Jenkins Job ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                        body: "Unit and integration tests failed. Please check the logs.",
                        to: "${env.EMAIL_RECIPIENTS}",
                        attachLog: true // Attach Jenkins build log
                    )
                }
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis with SonarQube...'
                echo 'Tool: SonarQube'
                // Simulate code analysis
                bat 'echo "Performing Code Analysis"'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running security scan using OWASP Dependency-Check...'
                echo 'Tool: OWASP Dependency-Check'
                // Simulate security scan log creation
                bat 'echo "Running Security Scan"'
            }
            post {
                success {
                    emailext (
                        subject: "Security Scan SUCCESS: Jenkins Job ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                        body: "Security scan passed successfully.",
                        to: "${env.EMAIL_RECIPIENTS}",
                        attachLog: true // Attach Jenkins build log
                    )
                }
                failure {
                    emailext (
                        subject: "Security Scan FAILURE: Jenkins Job ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                        body: "Security scan failed. Please check the logs.",
                        to: "${env.EMAIL_RECIPIENTS}",
                        attachLog: true // Attach Jenkins build log
                    )
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying the application to staging (e.g., AWS EC2 instance)...'
                echo 'Tool: AWS CLI'
                // Simulate deployment step
                bat 'echo "Deploying to Staging"'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests in the staging environment...'
                echo 'Tool: Selenium for testing'
                // Simulate integration tests
                bat 'echo "Running Integration Tests on Staging"'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying the application to production (e.g., AWS EC2 instance)...'
                echo 'Tool: AWS CLI'
                // Simulate production deployment
                bat 'echo "Deploying to Production"'
            }
        }
    }

    post {
        always {
            // Jenkins will automatically handle attaching the complete build log
            emailext (
                subject: "${currentBuild.result}: Jenkins Job ${env.JOB_NAME} [${env.BUILD_NUMBER}]",
                body: "The pipeline has completed with status: ${currentBuild.result}. Please check the attached logs.",
                to: "${env.EMAIL_RECIPIENTS}",
                attachLog: true // Attach the entire Jenkins build log
            )
        }
    }
}
