podTemplate(label: 'builder',
            containers: [
                    containerTemplate(name: 'docker', image: 'docker', command: 'cat', ttyEnabled: true),
            ]) {
        node('builder') {
            stage('Build docker image') {
                container('docker') {
                        sh "cd apis/userprofile"
                        sh "docker build . -t userProfile"
                    }
                }
            }
        }
