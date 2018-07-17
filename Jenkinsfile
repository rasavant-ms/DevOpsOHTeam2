pipeline {
  agent any
  stages {
    stage('Build Node') {
      steps {
        sh '''cd apis/userprofile
docker build -t userProfile'''
      }
    }
  }
}