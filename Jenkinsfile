pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat 'docker build -t image1 .'
            }
        }
        stage ("Tag") {
            steps {
                bat 'docker tag image1 shaikmustafa/paytm:bank'
            }
        }
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        bat 'docker push shaikmustafa/paytm:bank'
                    }
                }
            }
        }
        
        stage ("Deploy") {
            steps {
                bat 'docker run -itd --name bank-app -p 1111:80 shaikmustafa/paytm:bank'
            }
        }
    }
}
