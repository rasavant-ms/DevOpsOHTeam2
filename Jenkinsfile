pipeline {
  agent any
  stages {
    stage('Build_poi') {
      agent any
      environment {
        IMAGE_NAME = 'ohdrteam02acr.azurecr.io/devopsoh/api-user:1.1'
      }
      steps {
        git(url: 'https://github.com/wsf11/DevOpsOHTeam2.git', branch: 'lumirand')
        dir(path: './apis/userprofile') {
          sh 'docker build . -t $IMAGE_NAME'
        }

      }
    }
    stage('CreateImage_poi') {
      environment {
        IMAGE_NAME = 'ohdrteam02acr.azurecr.io/devopsoh/api-user:1.0'
      }
      steps {
        script {
          withCredentials([azureServicePrincipal('Default_SP')]) {
            sh 'docker login ohdrteam02acr.azurecr.io -u $AZURE_CLIENT_ID -p $AZURE_CLIENT_SECRET'
            sh 'docker push $IMAGE_NAME'
          }
        }

      }
    }
    stage('Test_poi') {
      agent {
        docker {
          image 'node:8-alpine'
        }

      }
      steps {
        git(url: 'https://github.com/wsf11/DevOpsOHTeam2.git', branch: 'lumirand')
        dir(path: './apis/userprofile') {
          sh 'npm run-script test'
        }

      }
    }
  }
}