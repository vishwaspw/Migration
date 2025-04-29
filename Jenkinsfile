pipeline {
    agent any

    tools {
        maven 'VishwasMaven'  // 
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/vishwaspw/Migration.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Run Application') {
            steps {
                // Adjust the JAR name to match your project’s output
                sh 'java -jar target/Migration-1.0-SNAPSHOT.jar'
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
