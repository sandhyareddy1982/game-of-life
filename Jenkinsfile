node('master') {
    stage('Source Code Fetch') {
    git 'https://github.com/karjunreddy85/game-of-life'
}
	
	stage('Build') {
    sh 'mvn install'
}
	stage('Nexus Deploy') {
    nexusArtifactUploader artifacts: [[artifactId: 'Dev', classifier: '', file: 'gameoflife-web/target/gameoflife.war', type: 'war']], credentialsId: 'e15aa808-2478-4c67-b81a-3d6ca415d3b0', groupId: 'Dev', nexusUrl: '34.221.19.115:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'Gol', version: '1.$BUILD_ID'
}
	stage('Trigger Ansible') {
    ansiblePlaybook inventory: 'inventory', playbook: 'Playbook.yml'
}
	
}
