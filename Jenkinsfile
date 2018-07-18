pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
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
        stage('Build_trips') {
          environment {
            IMAGE_NAME_TRIPS = 'ohdrteam02acr.azurecr.io/devopsoh/api-trip:1.0'
          }
          steps {
            git(url: 'https://github.com/wsf11/DevOpsOHTeam2.git', branch: 'lumirand')
            dir(path: './apis/trips') {
              sh 'docker build . -t $IMAGE_NAME_TRIPS'
            }

          }
        }
        stage('Build_userprofile') {
          environment {
            IMAGE_NAME = 'ohdrteam02acr.azurecr.io/devopsoh/api-user:1.0'
          }
          steps {
            dir(path: './apis/userprofile') {
              sh 'docker build . -t $IMAGE_NAME'
            }

            git(url: 'https://github.com/wsf11/j2.git', branch: 'lumirand')
          }
        }
      }
    }
  }
}