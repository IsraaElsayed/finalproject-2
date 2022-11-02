pipeline {
  
    agent any

    stages 
    {
        stage('git checkout') 
        {
            steps {
   
                git 'https://github.com/IsraaElsayed/finalproject-2.git'
            }
        }
        
        stage('build') {
            steps {
                sh 'docker build -f dockerfile . -t esraaelsayed/nodejs:latest'
            }
        }
        
        stage('artifact') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub')]){
                sh 'docker push esraaelsayed/nodejs:latest'
            }                                                       
           }
        }
        
        stage('deloy') {
            steps 
            {

                #sh 'kubectl create namespace app'
                sh 'kubectl apply -f ./deployapp.yaml -n app'
                
                
            }
           }
        }
}
