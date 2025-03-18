
pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('ansible530')
    }
    stages { 
        stage('SCM Checkout') {
            steps{
            git 'https://github.com/shahjad-k/docker-project786.git'
            }
        }

        stage('Build docker image') {
            steps {  
                sh 'docker build -t ansible50/iccpnew:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push ansible530/iccpnew:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}

