pipeline{
    agent {
        label 'rhel-agent1'
    }
    tools {
        maven 'maven362'
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

