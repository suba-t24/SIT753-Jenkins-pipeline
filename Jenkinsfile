pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Installing dependencies and building the project with npm...'
                sh 'npm install'
                sh 'npm run build'  // Make sure your package.json has a "build" script
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests with npm...'
                sh 'npm test'  // Ensure you have test scripts configured in package.json
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
                sh 'npm audit --audit-level=moderate'  // Or use other tools like Snyk
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging environment...'
                // Add your deployment commands, e.g., scp, AWS CLI, SSH
                // sh 'scp -r ./dist user@staging-server:/var/www/app'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on Staging environment...'
                // Example: Run integration tests against staging URL
                // sh './run-integration-tests.sh'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production environment...'
                // Add your production deployment commands here
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
