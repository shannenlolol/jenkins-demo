pipeline {
    agent any   // run on the built-in Jenkins agent

    // Optional: only if you configure NodeJS in Jenkins tools
    tools {
        nodejs 'default'
    }

    environment {
        NODE_ENV = 'test'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'npm ci'
            }
        }

        stage('Run tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Build app') {
            steps {
                sh 'npm run build'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished (success or failure).'
        }
        success {
            echo 'All good. Ready to deploy.'
        }
        failure {
            echo 'Something went wrong. Check the logs.'
        }
    }
}
