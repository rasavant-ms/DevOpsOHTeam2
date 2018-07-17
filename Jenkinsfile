podTemplate(label: 'builder',
            containers: [
                    containerTemplate(name: 'docker', image: 'docker', command: 'cat', ttyEnabled: true),
            ]) {
        node('builder') {
            stage('Build docker image') {
                git 'https://github.com/wsf11/DevOpsOHTeam2.git'
                container('docker') {
                        sh "docker build ./api/userprofile/Dockerfile -t userprofile"
                    }
                }
            }
        }
