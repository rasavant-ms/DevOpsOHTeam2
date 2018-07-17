pipeline {
  agent {
    docker {
      image 'docker:stable'
    }

  }
  stages {
    stage('Build Node') {
      steps {
        sh '''cd apis/userprofile
docker build . -t userProfile'''
      }
    }
  }
}