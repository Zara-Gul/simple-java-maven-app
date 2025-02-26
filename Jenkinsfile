pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Zara-Gul/simple-java-maven-app'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Deploy') {
            when {
                expression { currentBuild.result == null || currentBuild.result == 'SUCCESS' }
            }
            steps {
                echo 'Tests Passed! Deploying application...'

                echo 'Running application as a standalone JAR...'
                bat 'java -jar target/my-app-1.0-SNAPSHOT.jar' 
            }
        }
    }
}
