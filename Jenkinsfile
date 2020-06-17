pipeline { 
    agent any  
    stages { 
        stage('Checkout') { 
            steps { 
               Checkout scm
            }
        }
        stage('Build') {  
            steps {
              echo "hello world"
            }
        }
        // stage('Upload') {
        //     steps {
        //       sh "docker tag lyt-login-portal:latest 695292474035.dkr.ecr.us-west-2.amazonaws.com/lyt-loging-portal:latest"
        //       sh "docker push 695292474035.dkr.ecr.us-west-2.amazonaws.com/lyt-loging-portal:latest"
        //       echo "Image "
        //     }
        // }
        // stage('Deploy') {
        //     steps {
        //       sh "ecs deploy my-cluster my-service"
        //     }
        // }
    }
}