pipeline {
 environment { 
        registry = "williamc160/practical-2" 
        registryCredential = 'dockerhub' 
        dockerImage = 'practical-2' 

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
  stage('Push image') {
    steps{
    withDockerRegistry([ credentialsId: "williamc160", url: "https://hub.docker.com/repository/docker/williamc160/practical-2" ]) {
    bat "docker push williamc160/practical-2:build"
      }
    }
stage('Cleaning up') { 
      steps { 
      sh "docker rmi $registry:$BUILD_NUMBER" 
      }
    } 
  }
}
