pipeline {
    agent any
 stages {
  stage('Docker Build and Tag') {
           steps {
              
                sh 'docker build -t nginxtest:latest .' 
                  sh 'docker tag nginxtest nikhilnidhi/nginxtest:latest'
                sh 'docker tag nginxtest nikhilnidhi/nginxtest:$BUILD_NUMBER'
               
          }
        }
     
  stage('Publish image to Docker Hub') {
          
            steps {
        withDockerRegistry([ credentialsId: "dockerhub_id, url: "" ]) {
          sh  'docker push nikhilnidhi/nginxtest:latest'
          sh  'docker push nikhilnidhi/nginxtest:$BUILD_NUMBER' 
        }
                  
          }
        }
    }
}
