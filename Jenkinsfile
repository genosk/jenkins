pipeline {
    agent any

    environment {
        JAVA_HOME = '/usr/lib/jvm/jdk-25'  // Update with your JDK location if needed
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
    }

    stages {
        // Stage 1: Checkout Code from GitHub
        stage('Checkout') {
            steps {
                // Checkout code from the specified GitHub repository
                git branch: 'main', credentialsId: '9fb51a92-6680-4646-a8d0-cc9d75383fe0', url: 'https://github.com/genosk/jenkins.git'
            }
        }

        // Stage 2: Build the Project
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Use Maven to build the project (adjust if you're using Gradle or other tools)
                sh 'mvn clean install'
            }
        }

        // Stage 3: Test the Project
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Run tests using Maven (adjust if you're using a different testing tool like Gradle)
                sh 'mvn test'
            }
        }

        // Stage 4: Deploy the Application (optional)
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Add your deployment steps here (e.g., deploy to AWS, Docker, Heroku)
                // Example: sh 'aws deploy --bucket your-bucket --file your-app.zip'
            }
        }
    }

    post {
        success {
            echo 'Build and Tests Successful!'
        }
        failure {
            echo 'Build or Tests Failed.'
        }
        always {
            echo 'Pipeline finished.'
        }
    }
}
