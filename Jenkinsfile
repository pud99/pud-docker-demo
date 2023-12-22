pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('docker_global_access')
    }
    stages { 

        stage('Build docker image') {
            steps {  
                sh 'docker build -t pudpanw/pud-monk_in_cloud-flask_lab:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push pudpanw/pud-monk_in_cloud-flask_lab:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
