pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('benzone')
    }
    stages { 
        stage('SCM Checkout') {
            steps{
            git 'https://github.com/Telzone/kops.git'
            }
        }

        stage('Build docker image') {
            steps {  
                sh 'docker build -t iccpinfotech/iccpnew:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-Abhishek@123'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push iccpinfotech/iccpnew:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }

