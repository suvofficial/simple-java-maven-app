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
                sh "mvn clean install"
            }
        }
        stage ('Test') {
            steps{
            sh "mvn test"
            }
        }
    }
 }
//justtomakesure
