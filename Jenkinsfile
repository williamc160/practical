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
    withCredentials([usernamePassword( credentialsId: 'williamc160', usernameVariable: 'USER', passwordVariable: 'PASSWORD')]) {
        def registry_url = "https://hub.docker.com/repository/docker/williamc160/practical-2"
        bat "docker login -u $USER -p $PASSWORD ${registry_url}"
        docker.withRegistry("http://${registry_url}", "docker-hub-credentials") {
            // Push your image now
            bat "docker push williamc160/practical-2:$BUILD_NUMBER"
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
