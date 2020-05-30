node('master') {
    stage('Source Code Checkout') {
    git 'https://github.com/arjunkundur/game-of-life.git'
}
stage('Maven - Build') {
    sh label: '', script: 'mvn install'
}
stage('Nexus Deploy') {
    nexusArtifactUploader artifacts: [[artifactId: 'Dev', classifier: '', file: 'gameoflife-web/target/gameoflife.war', type: 'war']], credentialsId: 'e94b66b3-d068-46b9-8543-a6c18451e4df', groupId: 'Dev', nexusUrl: '18.237.74.83:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'GameofLife', version: '$BUILD_ID'
}

}
