pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the code...'
                // In a real scenario, you would run your build commands here.
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests...'
                // In a real scenario, you would run your unit tests here.
                echo 'Running integration tests...'
                // In a real scenario, you would run your integration tests here.
            }

            post {
                success {
                    emailext (
                        to: "mitultandon2000@gmail.com",
                        subject: "Testing of current build  on : Pipeline ${currentBuild.fullDisplayName} ",
                        body: "Testing of  ${env.TESTING_ENVIRONMENT} in ${currentBuild.fullDisplayName} has completed. \n\n Check console output at: ${env.BUILD_URL}", 
                        attachLog: true
                    )
                }
                failure {
                    emailext (
                        to: "mitultandon2000@gmail.com",
                        subject: "Testing of current build on : Pipeline ${currentBuild.fullDisplayName}",
                        body: "Testing of latest commit ${env.TESTING_ENVIRONMENT} in ${currentBuild.fullDisplayName} has failed.",
                        attachLog: true
                    )
                }
            }
        }

        
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code...'
                // In a real scenario, you would run your code analysis tools here.
            }
        }
        
        stage('Security Scan') {
            steps {
                echo 'Performing security scan...'
                // In real scenario, you would run your security scan tools here.
            }
            post {
            success {
                emailext (
                    to: "mitultandon2000@gmail.com",
                    subject: "Security scan is completed: Pipeline ${currentBuild.fullDisplayName}",
                    body: "Security scan in   in ${currentBuild.fullDisplayName} has completed . \n\n Check console output at: ${env.BUILD_URL}", 
                    attachLog: true
                )
            }
            failure {
                emailext (
                    to: "mitultandon2000@gmail.com",
                    subject: "Security scan failure: Pipeline ${currentBuild.fullDisplayName}",
                    body: "Security scan in ${currentBuild.fullDisplayName} has failed.",
                    attachLog: true
                )
            }
        }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server...'
                // In a real scenario, you would deploy your application to staging here.
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                // In a real scenario, you would run integration tests on the staging environment here.
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production server...'
                // In a real scenario, you would deploy your application to production here.
            }
        }
    }

    post {
        always {
            // Send email notification
            emailext(
                subject: "Build ${currentBuild.result}: ${env.JOB_NAME} ${env.BUILD_NUMBER}",
                body: "Build ${currentBuild.result}: ${env.JOB_NAME} ${env.BUILD_NUMBER} \n\n Check console output at: ${env.BUILD_URL}",
                to: "mitultandon2000@gmail.com", // Replace with your email address
                attachLog: true
            )
        }
    }
}
