podTemplate(label: 'builder',
            containers: [
                    containerTemplate(name: 'userprofile', image: 'node:8-alpine', command: 'cat', ttyEnabled: true),
                    containerTemplate(name: 'trips', image: 'golang:1.10.3', command: 'cat', ttyEnabled: true),
            ]) {
        node('builder') {
            stage('userprofile') {
                git 'https://github.com/wsf11/DevOpsOHTeam2.git'
                container('userprofile') {
                            dir ("./apis/userprofile"){
                                    sh "npm install"
                                    sh "npm run-script test"
                                    sh "npm run-script lint"
                            }
                    }
            }
             stage('trips') {
                git 'https://github.com/wsf11/DevOpsOHTeam2.git'
                container('trips') {
                        sh """
                        mkdir /go/src/github.com/Azure-Samples/openhack-devops-team -p
                        cp -R . /go/src/github.com/Azure-Samples/openhack-devops-team
                        cd /go/src/github.com/Azure-Samples/openhack-devops-team/apis/trips
                        ls
                        curl https://glide.sh/get | sh
                        glide install
                        go build
                        go test ./test
                        """
               }
            }
        }
}
