pipeline {
    agent any

    tools {
        nodejs 'NodeJS'
    }

    parameters {
        string(name: 'BRANCH_NAME', defaultValue: 'main')
        string(name: 'BUILD_ENV', defaultValue: 'dev')
        string(name: 'STUDENT_NAME', defaultValue: 'Arsal Temuri')
    }

    environment {
        APP_VERSION = "1.0.0"
    }

    stages {
        stage('Install Dependencies') {
            steps {
                echo "Installing dependencies..."
                bat "npm install"
            }
        }

        stage('Build') {
            steps {
                echo "Building Calculator App v${APP_VERSION} on branch ${params.BRANCH_NAME}"
            }
        }

        stage('Unit Test') {
            when {
                expression { return params.BUILD_ENV == 'dev' }
            }
            steps {
                echo 'Running tests...'
                bat "npm test"
            }
        }

        stage('Deploy') {
            steps {
                echo 'Simulating deployment...'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
        }
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
