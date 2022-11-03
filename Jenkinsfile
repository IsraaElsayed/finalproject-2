pipeline {
    agent any

    stages {
        
        stage('build') {
            steps {
                sh 'docker build . -t esraaelsayed/nodejs:latest'
            }
        }
        
        stage('artifact') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker', passwordVariable: 'PASSWORD', usernameVariable: 'USERNAME')]) {

                    sh 'docker push esraaelsayed/nodejs:latest'
                }               
                
                
                
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
}
   
