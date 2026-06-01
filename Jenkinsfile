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
            sh '/usr/local/bin/docker build -t flask-demo .'
        }
     }
     stage('Deploy Container'){
        steps{
           sh '''
           /usr/local/bin/docker rm -f flask-demo || true
           /usr/local/bin/docker run -d \
           --name flask-demo \
           -p 5001:5000 \
           flas-demo
           '''
        }
     }
   }
}  
