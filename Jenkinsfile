pipeline {
    agent any

    environment {
        PATH = "/opt/homebrew/bin:$PATH"
        }

    stages {
        stage('Build') {
            steps {
                echo 'Installing dependencies and building the project with npm...'
                sh 'npm install'
                sh 'npm run build' 
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests with npm...'
                sh 'npm test'  
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing static code analysis with SonarQube...'
                // Example SonarQube scanner for JavaScript
                // withSonarQubeEnv('MySonarQubeServer') {
                //     sh 'sonar-scanner'
                // }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running security scan using npm audit...'
		// Tool: npm audit
                sh 'npm audit --audit-level=moderate'  
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to staging environment on AWS EC2...'
                // Add your deployment commands, e.g., scp, AWS CLI, SSH
                // sh 'scp -r ./dist user@staging-server:/var/www/app'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging using Newman (Postman CLI)...'
                // Tool: Postman / Newman
                // sh './run-integration-tests.sh'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to production environment on AWS EC2...'
                // Tool: AWS CLI / SCP
                // sh 'scp -r ./dist user@production-server:/var/www/app'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up workspace...'
            cleanWs()
        }
    }
}
