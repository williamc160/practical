pipeline {
 environment { 
        registry = "williamc160/practical-2" 
        registryCredential = 'dockerhub' 
        dockerimage = 'practical-2' 
        def registry_url = "https://index.docker.io/v1/"
  }
  agent any
  stages {
    stage('Building our image') {
      steps{
         script { 
            dockerimage = docker.build registry + ":$BUILD_NUMBER" 
     }
    }
   }
   stage('Push image') {
     steps{
     withDockerRegistry([ credentialsId: "dockerhub", url: "https://index.docker.io/v1/"]) { 
     sh "docker push dockerimage"
    } 
   }
  }
}
}
