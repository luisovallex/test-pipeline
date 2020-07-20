pipeline { 
//agent { label 'build-example' }
    // agent any
    // parameters {
    //     string(name: 'GIT_REV', defaultValue: 'latest', description: 'The git commit you want to build (Keep \'latest\' value for latest commit)')
    // }
    // options {
    //     disableConcurrentBuilds()
    // }
    // triggers {
    //     pollSCM("* * * * *")
    // }
    stages { 
        stage('Checkout') { 
            steps { 
              checkout scm
            }
        }
        stage('Build') {  
            steps {
              sh "echo 'hello world'"
            }
    }
}