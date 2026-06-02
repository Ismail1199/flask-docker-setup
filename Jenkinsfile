pipeline {
    agent any

    environment {
        PATH = "/usr/local/bin:/Applications/Docker.app/Contents/Resources/bin:/usr/bin:/bin:/usr/sbin:/sbin"
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Debug') {
            steps {
                sh '''
                echo "PATH=$PATH"
                which docker
                which docker-credential-desktop
                docker --version
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-demo .'
            }
        }

        stage('Deploy to Kubernetes') {
    steps {
        sh '''
        kubectl apply -f deployment.yaml
        kubectl apply -f service.yaml
        kubectl rollout restart deployment flask-demo
        '''
    }
}
        }
    }
}
