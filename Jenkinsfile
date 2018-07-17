podTemplate(label: 'builder',
            containers: [
                    containerTemplate(name: 'poi', image: 'microsoft/dotnet:2.1-aspnetcore-runtime', command: 'cat', ttyEnabled: true),
            ]) {
        node('builder') {
            stage('poi') {
                git url: 'https://github.com/wsf11/DevOpsOHTeam2.git', branch: 'rjdev'
                container('poi') {
                            dir ("./apis/poi"){
                                    sh "dotnet restore"
                                    sh "dotnet publish -c Release -o out"
                            }
                    }
                }
            }
        }
