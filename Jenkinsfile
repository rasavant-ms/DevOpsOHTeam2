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
             stage('trips') {
                git 'https://github.com/wsf11/DevOpsOHTeam2.git'
                container('trips') {
                            dir ("./apis/trips") {
                                    sh "ls"
                                    sh "curl https://glide.sh/get | sh"
                                    sh "glide install --skip-test"
                                    sh "CGO_ENABLED=0 GOOS=linux go build -o main ."
                                    sh "ls"
                            }
                    }
                }
            }
        }
}
