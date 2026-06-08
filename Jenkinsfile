pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                bat 'docker build -t image3 .'
            }
        }
        stage ("Tag") {
            steps {
                bat 'docker tag image3 shaikmustafa/paytm:movie'
            }
        }
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub') {
                        bat 'docker push shaikmustafa/paytm:movie'
                    }
                }
            }
        }
        
        stage ("Deploy") {
            steps {
                bat 'docker run -itd --name movie-app -p 3333:80 shaikmustafa/paytm:movie'
            }
        }
    }
}
