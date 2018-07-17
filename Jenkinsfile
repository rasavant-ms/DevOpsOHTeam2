podTemplate(label: 'builder',
            containers: [
                    containerTemplate(name: 'docker', image: 'docker:stable-dind', command: 'cat', ttyEnabled: true),
            ]) {
        node('builder') {
            stage('Build docker image') {
                git 'https://github.com/wsf11/DevOpsOHTeam2.git'
                container('docker') {
                        sh "docker build ./apis/userprofile/ -t userprofile"
                    }
                }
            }
        }
