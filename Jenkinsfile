pipeline {
    agent any
 
    parameters {
        choice(name: 'BUILD_TOOL', choices: ['maven', 'gradle'], description: 'Choose Build Tool')
    }
 
    environment {
        BUILD_TOOL_CMD = params.BUILD_TOOL == 'maven' ? 'mvn clean package' : 'gradle build'
    }
 
    stages {
        stage('Checkout') {
            steps {
                echo "Cloning the project from SCM..."
                checkout scm
            }
        }
 
        stage('Build') {
            steps {
                echo "Building the project with ${params.BUILD_TOOL}..."
                sh "${BUILD_TOOL_CMD}"
            }
        }
 
        stage('Test') {
            steps {
                echo "Running tests..."
                sh 'mvn test'
            }
        }
 
        stage('Package') {
            steps {
                echo "Packaging the project..."
                sh 'mvn clean package'
            }
        }
 
        stage('Deploy') {
            steps {
                echo "Deploying to the Test Environment (placeholder)..."
                echo "Deployment complete!"
            }
        }
    }
 
    post {
        success {
            echo "Pipeline executed successfully!"
        }
        failure {
            echo "Pipeline execution failed!"
        }
    }
} 
