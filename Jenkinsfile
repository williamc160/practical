pipeline {
  environment {
    DOCKERHUB_CREDENTIALS = ('WILLIAMC160')
}
  agent any
  stages {
    stage('Building our image') {
      steps{
        sh 'docker build -t williamc160/practical-2:latest .'
    }
  }
  stage('login'){
    steps{
      sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdir'
    }
  }
  stage('push'){
    steps{
      sh 'docker push williamc160/practical-2:latest'
    }
  }
}

  post {
    always{
      sh 'docker logout'
    }
  }
}
