pipeline { 
    agent any  
    stages { 
        stage('Checkout') { 
            steps { 
              checkout scm
            }
        }
        stage('Build') {  
            steps {
              sh "docker build -t lyt-test:latest ."
              sh "docker tag lyt-test:latest 695292474035.dkr.ecr.us-west-2.amazonaws.com/lyt-loging-portal:${env.GIT_COMMIT.take(7)}"
              sh "docker tag lyt-test:latest 695292474035.dkr.ecr.us-west-2.amazonaws.com/lyt-loging-portal:latest"
              sh "docker push 695292474035.dkr.ecr.us-west-2.amazonaws.com/lyt-loging-portal:latest"
              sh "docker push 695292474035.dkr.ecr.us-west-2.amazonaws.com/lyt-loging-portal:${env.GIT_COMMIT.take(7)}"
            }
        }
        stage('Ecr login') {
            steps {
              sh "aws ecr get-login-password --region us-west-2 | docker login --username AWS --password-stdin 695292474035.dkr.ecr.us-west-2.amazonaws.com"
            }
        }
        stage('Push to ecr') {
            steps {
              sh "docker push 695292474035.dkr.ecr.us-west-2.amazonaws.com/lyt-loging-portal:latest"
              sh "docker push 695292474035.dkr.ecr.us-west-2.amazonaws.com/lyt-loging-portal:${env.GIT_COMMIT.take(7)}"
            }
        }
        stage('Cleanup jenkins') {
            steps {
              sh "docker rmi lyt-test:latest"
              sh "docker rmi 695292474035.dkr.ecr.us-west-2.amazonaws.com/lyt-loging-portal:${env.GIT_COMMIT.take(7)}"
              sh "docker rmi 695292474035.dkr.ecr.us-west-2.amazonaws.com/lyt-loging-portal:latest"
            }
        }
    }
}