pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                // Example Maven build command
                sh 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running Unit and Integration Tests with JUnit...'
                // Run tests using Maven Surefire plugin or equivalent
                sh 'mvn test'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing static code analysis with SonarQube...'
                // Example SonarQube scanner command
                // withSonarQubeEnv('MySonarQubeServer') {
                //     sh 'mvn sonar:sonar'
                // }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running security scan using OWASP Dependency-Check...'
                // Example command to run OWASP Dependency-Check
                sh 'dependency-check.sh --project MyApp --scan .'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging environment (e.g., AWS EC2)...'
                // Example SSH deploy or AWS CLI deploy commands here
                // sh 'scp target/myapp.jar user@staging-server:/deploy/path'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on Staging environment with Selenium/Postman...'
                // Placeholder for running integration tests against staging
                // sh './run-integration-tests.sh'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production environment...'
                // Deploy commands for production environment
                // sh 'scp target/myapp.jar user@production-server:/deploy/path'
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
