pipeline{
    agent {
        label 'rhel-agent1'
    }
    tools {
        maven 'maven362'
    }
    environment {
        target_user= "ec2-user"
        target_server= "172.31.80.4"
    }
    options {
        timeout(10)
        buildDiscarder logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '5', numToKeepStr: '5')
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build'){
            steps{
                sh "mvn clean install -DskipTests"
            }
        }
        stage('Test') {
            steps {
                sh "mvn test"
                junit allowEmptyResults: true, testResults: 'target/surefire-reports/*.xml'
            }
        }
        stage('Deploy'){
            steps{
            echo "Deploying to Dev Environmnet"
            sshagent(['maven-cd-key']) {
                sh "scp -o StrictHostKeyChecking=no target/my-app-1.0-SNAPSHOT.jar $target_user@$target_server:/home/ec2-user"
             }
            }
        }
    }
    post{
        always{
            deleteDir()
        }
        success{
            echo "The job is successful"
        }
        failure{
            echo "sendmail -s Maven job Failed receipient@mycompany.com"
        }
    }
}

