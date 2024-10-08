pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Building the project...'
                    // Example: mvn clean install
                }
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                script {
                    echo 'Running unit and integration tests...'
                    // Example: mvn test
                }
            }
            post {
                always {
                    emailext(
                        subject: "Jenkins Pipeline - Unit and Integration Tests: ${currentBuild.fullDisplayName}",
                        body: "Build Status: ${currentBuild.currentResult}\n\nStage: Unit and Integration Tests",
                        recipientProviders: [[$class: 'DevelopersRecipientProvider']],
                        to: 'chamindub69@gmail.com',
                        attachLog: true
                    )
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                script {
                    echo 'Analyzing the code quality...'
                    // Example: mvn sonar:sonar
                }
            }
        }
        
        stage('Security Scan') {
            steps {
                script {
                    echo 'Running security scan...'
                    // Example: mvn dependency-check:check
                }
            }
            post {
                always {
                    emailext(
                        subject: "Jenkins Pipeline - Security Scan: ${currentBuild.fullDisplayName}",
                        body: "Build Status: ${currentBuild.currentResult}\n\nStage: Security Scan",
                        recipientProviders: [[$class: 'DevelopersRecipientProvider']],
                        to: 'chamindub69@gmail.com',
                        attachLog: true
                    )
                }
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                script {
                    echo 'Deploying to staging environment...'
                    // Example: deploy to AWS EC2
                }
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                script {
                    echo 'Running integration tests on staging...'
                    // Example: run integration tests on staging
                }
            }
        }
        
        stage('Deploy to Production') {
            steps {
                script {
                    echo 'Deploying to production environment...'
                    // Example: deploy to production server
                }
            }
        }
    }
}