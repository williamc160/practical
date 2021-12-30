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
  stage('Push image') {
  steps{
        withDockerRegistry([ credentialsId: "dockerhub", url: "https://index.docker.io/v1/" ]) {
        sh "docker push williamc160/practical-2"
     }
    }
   }
  stage('Build-Test'){
  steps {
        script {
        try {                           
        def status = 0
        status = sh(returnStdout: true, script: "container-test test --image 'dockerImage' --config './practical/Utest.yaml' --json | jq .Fail") as Integer
        if (status != 0) {                            
        error 'Image Test has failed'
                          }
        } catch (err) {
        error "Test ERROR: container has failed, you messed up"
      echo err
    } 
   }
  }
 }
}
}
