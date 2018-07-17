podTemplate(label: 'builder',
            containers: [
                    containerTemplate(name: 'poi', image: 'microsoft/dotnet:2.1-aspnetcore-runtime', command: 'cat', ttyEnabled: true),
            ]) {
        node('builder') {
            stage('poi') {
                git url: 'https://github.com/wsf11/DevOpsOHTeam2.git', branch: 'rjdev'
                container('poi') {
                            dir ("./apis/poi"){
                                    bat "nuget restore poi.sln"
                                    bat "\"${tool 'MSBuild'}\" poi.sln /p:Configuration=Release /p:Platform=\"Any CPU\"
                            }
                    }
                }
            }
        }
