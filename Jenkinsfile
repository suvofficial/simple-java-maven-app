pipeline {
    agent {
        label 'agent1'
    }
    tools {
        maven 'maven362'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh "mvn clean install"
            }
        }
        stage('Test') {
            sh "mvn test"
        }
    }
}
