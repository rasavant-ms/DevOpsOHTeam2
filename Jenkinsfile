podTemplate(label: 'builder',
            containers: [
                    containerTemplate(name: 'userprofile', image: 'node:6.3', command: 'cat', ttyEnabled: true),
            ]) {
        node('builder') {
            stage('Build docker image') {
                git 'https://github.com/wsf11/DevOpsOHTeam2/tree/rjdev'
                container('userprofile') {
                        sh "node -v"
                    }
                }
            }
        }
