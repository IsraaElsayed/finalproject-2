
pipeline {
    agent any

    stages {
        
        stage('build') {
            steps {
                sh 'docker build . -t israaelsayed/nodejs:latest'
            }
        }
        
        stage('artifact') {
            steps {
                // This step should not normally be used in your script. Consult the inline help for details.
                    withDockerRegistry(credentialsId: 'docker',url:'') {
                       sh 'docker push israaelsayed/nodejs:latest'
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
   
