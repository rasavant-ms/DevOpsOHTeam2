podTemplate(label: 'builder',
            containers: [
                    containerTemplate(name: 'userprofile', image: 'node:8-alpine', command: 'cat', ttyEnabled: true),
            ]) {
        node('builder') {
            stage('userprofile') {
                git 'https://github.com/wsf11/DevOpsOHTeam2.git'
                container('userprofile') {
                            dir ("./apis/userprofile"){
                                    sh "ls"
                                    sh "npm install"
                                    sh "npm test"
                                    sh "npm lint"
                            }
                    }
                }
            }
        }
