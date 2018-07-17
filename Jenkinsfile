podTemplate(label: 'builder',
            containers: [
                    containerTemplate(name: 'userprofile', image: 'node:8-alpine', command: 'cat', ttyEnabled: true),
                    containerTemplate(name: 'trips', image: 'golang:1.10.3', command: 'cat', ttyEnabled: true),
                    containerTemplate(name: 'poi', image: 'microsoft/dotnet:2.1-sdk', command: 'cat', ttyEnabled: true),

            ]) {
        node('builder') {
            stage('poi') {
                git url: 'https://github.com/wsf11/DevOpsOHTeam2.git', branch: 'rjdev'
                container('poi') {
                            dir ("./apis/poi/web"){
                                    sh "dotnet restore"
                                    sh "dotnet publish -c Release -o out"
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
            stage('poi') {
                git url: 'https://github.com/wsf11/DevOpsOHTeam2.git'
                container('poi') {
                            dir ("./apis/poi/web"){
                                    sh "dotnet restore"
                                    sh "dotnet publish -c Release -o out"
                            }
                    }
                }
            }
        }
}
