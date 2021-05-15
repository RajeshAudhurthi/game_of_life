node{
    // some block
    stage('clone openmrs') {
    // some block
    git 'https://github.com/openmrs/openmrs-core.git'
}
    stage('build war file') {
    // some block
    sh 'mvn package'
}
    stage('Junit results') {
    // some block
    junit 'web/target/surefire-reports/*.xml' 
}
    stage('Archive the artifacts war file') {
    // some block
    archiveArtifacts artifacts: 'webapp/target/openmrs.war', followSymlinks: false
}
    stage('SonarQube analysis') {
    // some block
    withSonarQubeEnv('SonarQube') {
    sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
    }
}
    stage('Artifactory'){
    sh "curl -u admin:Rajesh@123 -T /var/lib/jenkins/workspace/openmrs-pipeline-scripted/webapp/target/*.war http://13.127.43.8:8082/artifactory/openmrs/openmrs.war"
}
}
node('ansible_slave){
    stage('clone openmrs yml') {
    // some block
    git 'https://github.com/RajeshAudhurthi/game_of_life.git'
}
    stage('run playbook') {
    // some block
    sh 'ansible-playbook openmrs.yml'
}
}
