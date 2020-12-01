peline {
    agent any
    triggers {plllSCM('*****') }
    options {
       timestamps()
    }
    stages {
        stage('Build a Docker Image'){
            steps {
                sh ("docker build -t testapp:dev.${env.BUILD_NUMBER}.")
            }

        }
        stage('Stop docker container'){
            steps {
                sh("docker stop myapp")
            }

        }
        stage('Deploy app){
            steps {
                sh("docker run --name=testapp --rm -d -p 8081:5000 testapp:dev.${env.BUILD_NUMBER}.")
            }
        }
     }
}   
