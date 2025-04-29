pipeline {
    agent any

    tools {
        maven 'VishwasMaven'  // Make sure this matches your Jenkins Maven tool
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
                // ✅ Corrected jar name
                sh 'java -jar target/MyMavenApp2-1.0-SNAPSHOT.jar'
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
