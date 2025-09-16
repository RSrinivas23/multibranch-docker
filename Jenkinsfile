pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image3 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image3 rsrinivas23/paytm:movie'
            }
        }
        stage('push') {
            steps {
               script {
                   withDockerRegistry(credentialsId: 'dockerhub') {
                     sh 'docker push rsrinivas23/paytm:movie'
}
               }
            }
        }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name movie-app -p 3333:80 rsrinivas23/paytm:movie'
            }
        }
    }
}
