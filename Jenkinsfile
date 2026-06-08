pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat 'docker build -t image2 .'
            }
        }
        stage ("Tag") {
            steps {
                bat 'docker tag image2 shaikmustafa/paytm:bus'
            }
        }
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        bat 'docker push shaikmustafa/paytm:bus'
                    }
                }
            }
        }
    
    }
}
