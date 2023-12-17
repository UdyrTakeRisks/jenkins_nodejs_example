pipeline {
    agent any
    environment{
        DOCKERHUB_CREDENTIALS= credentials('docker-credentials-from-jenkins')
    }
    stages {
        stage('CI') {
            steps {

               sh "echo ${DOCKERHUB_CREDENTIALS_PSW} | docker login -u ahmeddalii --password-stdin"
               sh "pwd"
               sh "ls"
               sh "docker build -f dockerfile -t nodeapp-img:1.0 ."
               sh "docker push nodeapp-img:1.0"
                }
            }
        
        stage('CD') {
            steps {
               sh "echo ${DOCKERHUB_CREDENTIALS_PSW} | docker login -u ahmeddalii --password-stdin"
               sh "docker run -d --name node-container -p 3000:3000 nodeapp-img:1.0"
            }
        }
    }
        
    }
