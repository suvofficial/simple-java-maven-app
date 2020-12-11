pipeline{
    agent{
        label 'rhel-agent1'
    }
    tools {
        maven 'maven362'
    }
    stages{
        stage('Checkout'){
            steps{
                checkout scm
            }
        }
        stage('Build'){
            steps{
                sh "mvn clean install -DskipTests"
            }
        }
        stage ('Test') {
            steps{
            sh "mvn test"
            }
        }
        stage('Post tasks'){
            steps{
                sh "echo send an email"
            }
        }
    }
 }
//test git-jenkins
