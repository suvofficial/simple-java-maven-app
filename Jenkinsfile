pipeline{
    agent{
        label 'rhel-agent1'
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
    }
    
}
