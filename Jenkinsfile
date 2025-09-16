pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image1 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image1 rsrinivas23/paytm:bank'
            }
        }
       stage('push') {
            steps {
               script {
                   withDockerRegistry(credentialsId: 'dockerhub') {
                     sh 'docker push rsrinivas23/paytm:bank'
}
               }
            }
        }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank-app -p 1111:80 rsrinivas23/paytm:bank'
            }
        }
    }
}
