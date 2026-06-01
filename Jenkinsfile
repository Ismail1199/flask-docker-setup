pipeline{
   agent any

   stages {
    stage('Checkout'){
        steps{
            checkout scm
        }
     }
     stage('Build Docker Image'){
        steps{
            sh 'docker build -t flask-demo .'
        }
     }
     stage('Deploy Container'){
        steps{
           sh '''
           docker rm -f flask-demo || true
           docker run -d \
           --name flask-demo \
           -p 5001:5000 \
           flas-demo
           '''
        }
     }
   }
}  
