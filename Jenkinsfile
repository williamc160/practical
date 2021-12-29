pipeline {
 environment { 
        registry = "williamc160/practical-2" 
        registryCredential = 'dockerhub' 
        dockerImage = 'practical-2' 
        def registry_url = "https://index.docker.io/v1/"

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
stage(login){
 steps{
        withCredentials([usernamePassword( credentialsId: 'williamc160', usernameVariable: 'USER', passwordVariable: 'PASSWORD')]){
        bat "docker login -u $USER -p $PASSWORD ${registry_url}"
        docker.withRegistry("https://index.docker.io/v1/", "dockerhub"){
    }
   }
  }

  stage('Push image') {
	steps{
            bat "docker push williamc160/practical-2:$BUILD_NUMBER"}
        }
    }
}
  stage('Cleaning up') {
      steps { 
      sh "docker rmi $registry:$BUILD_NUMBER" 
      }
    } 
  }
}
