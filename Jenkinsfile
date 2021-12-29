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
  stage('push'){
    steps{
      sh 'docker push williamc160/practical-2:latest'
    }
  }
}
}
