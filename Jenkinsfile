pipeline {
    agent any

    stages {
        stage('git checkout') {
            steps {
                git 'https://github.com/mahmoud254/jenkins_nodejs_example.git'
            }
        }
        
        stage('build') {
            steps {
                sh 'docker build -f dockerfile . -t esraaelsayed/nodejs:latest'
            }
        }
        
        stage('artifact') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub', passwordVariable: 'pass', usernameVariable: 'username')]){
                sh 'docker login -u ${username} -p ${pass}'
                sh 'docker push esraaelsayed/nodejs:latest'
                
                }
            }
        }
        
        stage('git app') {
            steps {
                git 'https://github.com/IsraaElsayed/finalproject-2.git'
            }
        }
        
        stage('deploy') {
            steps 
            {
                sh 'kubectl create namespace app'
                sh 'kubectl apply -f ./deployapp.yaml -n app'
                
                
            }
        }
    }