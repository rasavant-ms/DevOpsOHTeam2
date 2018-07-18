
node('master') {
    steps {
        stage('Build Docker Images') {
            parallel {
                stage('userprofile') {
                    git 'https://github.com/wsf11/DevOpsOHTeam2.git'
                    dir ("./apis/userprofile") {
                        sh "docker build . -t userprofile"
                    }
                }
                stage('trips') {
                    git 'https://github.com/wsf11/DevOpsOHTeam2.git'
                    dir("./apis/trips") {
                        sh "docker build . -t trips"
                    }
                }
                stage('poi') {
                    git url: 'https://github.com/wsf11/DevOpsOHTeam2.git'
                    dir ("./apis/poi/web") {
                        sh "docker build . -t poi"
                    }
                }
            }
        }
    }
}

