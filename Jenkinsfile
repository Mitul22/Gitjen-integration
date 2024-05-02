pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                // Build the code using Maven
                sh 'mvn clean package'
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests using JUnit
                sh 'mvn test'
                // Run integration tests using Selenium
                sh 'selenium run integration-tests'
            }
        }
        
        stage('Code Analysis') {
            steps {
                // Integrate SonarQube for code analysis
                sh 'sonar-scanner'
            }
        }
        
        stage('Security Scan') {
            steps {
                // Perform security scan using OWASP ZAP
                sh 'zap-cli --quick-scan --spider <target>'
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                // Deploy to AWS EC2 instance using AWS CLI
                sh 'aws ec2 deploy-to-staging'
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on staging environment
                sh 'selenium run integration-tests-staging'
            }
        }
        
        stage('Deploy to Production') {
            steps {
                // Deploy to AWS EC2 instance using AWS CLI
                sh 'aws ec2 deploy-to-production'
            }
        }
    }
}
