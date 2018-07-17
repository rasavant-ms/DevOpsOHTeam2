podTemplate(label: 'builder',
            containers: [
                    containerTemplate(name: 'userprofile', image: 'node:8-alpine', command: 'cat', ttyEnabled: true),
            ]) {
        node('builder') {
            stage('userprofile') {
                git 'https://github.com/wsf11/DevOpsOHTeam2/tree/rjdev'
                container('userprofile') {
                            dir ("./apis/userprofile"){
                                    sh "npm install"
                                    sh "npm run-script test"
                                    sh "npm run-script lint"
                            }
                    }
                }
            }
        }
