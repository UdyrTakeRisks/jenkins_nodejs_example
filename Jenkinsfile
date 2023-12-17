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
               sh "docker tag nodeapp-img:1.0 ahmeddalii/nodeapp-img:1.0"
               sh "docker push ahmeddalii/nodeapp-img:1.0"
                }
            }
        
        stage('CD') {
            steps {
               sh "echo ${DOCKERHUB_CREDENTIALS_PSW} | docker login -u ahmeddalii --password-stdin"
               sh "docker run -d --name node-container -p 3000:3000 ahmeddalii/nodeapp-img:1.0"
            }
        }
    }
        
    }
