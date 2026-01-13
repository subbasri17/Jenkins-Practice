pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Pulling code from GitHub...'
                git branch: 'main', url: 'https://github.com/Akshiv20/java-hello-world-with-maven.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the app...'
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying JAR to production...'
                sh 'mkdir -p /tmp/apps && cp target/my-sample-app-1.0-SNAPSHOT.jar /tmp/apps/ && echo "Deployment successful: JAR copied to /tmp/apps/"'
            }
        }
    }
}




