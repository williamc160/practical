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

  stage('push'){
    steps{
      sh 'docker push williamc160/practical-2:latest'
    }
  }
stage('Cleaning up') { 
      steps { 
      sh "docker rmi $registry:$BUILD_NUMBER" 
      }
    } 
  }
}
