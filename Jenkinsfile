node('master') {
    stage('Source Code Checkout') {
    git 'https://github.com/arjunkundur/game-of-life.git'
}
stage('Build') {
    withMaven {
    sh label: '', script: 'mvn install -DskipTests'
}
}
stage('Nexus Deploy') {
    nexusArtifactUploader artifacts: [[artifactId: 'Dev', classifier: '', file: 'gameoflife-web/target/gameoflife.war', type: 'war']], credentialsId: '83585a88-bac1-4905-9e0a-c9de123162ec', groupId: 'Dev', nexusUrl: '18.237.20.129:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'Gol', version: '$BUILD_ID'
}

}
