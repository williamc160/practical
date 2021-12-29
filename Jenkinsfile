pipeline {
 environment { 
        registry = "williamc160/practical-2" 
        registryCredential = 'dockerhub' 
        dockerImage = 'practical-2' 
        def registry_url = "https://index.docker.io/v1/"
        def app
  }
  agent any
  stages {
    stage('Building our image') {
      steps{
         script { 
            dockerImage = docker.build registry + ":$BUILD_NUMBER" 
     }
    }
   }
  stage('Test image') {           
    app.inside {            
             
             sh 'echo "Tests passed"'        
            }    
        }     
  stage('Push image') {
  steps{
        withDockerRegistry([ credentialsId: "dockerhub", url: "https://index.docker.io/v1/" ]) {
        bat "docker push williamc160/practical-2:2.0"
     }
    }
   }
  }
}
