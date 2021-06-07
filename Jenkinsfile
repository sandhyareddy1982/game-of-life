node('master') {
    stage('Source Code CheckOut') {
    git 'https://github.com/karjunreddy85/game-of-life'
}
	
	stage('Build') {
    sh 'mvn install'
}
	stage('Nexus Deploy') {
    nexusArtifactUploader artifacts: [[artifactId: 'Dev', classifier: '', file: 'gameoflife-web/target/gameoflife.war', type: 'war']], credentialsId: '55f67dc4-2619-4a05-aa1a-bd465ce1d3dc', groupId: 'Dev', nexusUrl: '18.236.142.130:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'Gol', version: '$BUILD_ID'
}
stage('Prod Deployment') {
    ansiblePlaybook extras: '-e BUILD_ID=$BUILD_ID', inventory: 'inventory', playbook: 'Playbook.yml'
}
}
