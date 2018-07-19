pipeline {
  agent any
  stages {
    stage('Build_poi') {
      environment {
        IMAGE_NAME = 'ohdrteam02acr.azurecr.io/devopsoh/api-poi:1.0'
      }
      steps {
        git(url: 'https://github.com/wsf11/DevOpsOHTeam2.git', branch: 'lumirand')
        dir(path: './apis/poi/web') {
          sh 'docker build . -t $IMAGE_NAME'
        }

      }
    }
    stage('Deploy_poi') {
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
  }
}