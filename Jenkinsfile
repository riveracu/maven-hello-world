pipeline {
agent any
tools {
// Install the Maven version configured as "Maven 3.6.3" and add it to the path.
maven "Maven 3.8.1"
}
stages {
stage('Build') {
steps {
// Get some code from a GitHub repository
git 'https://github.com/riveracu/maven-hello-world.git'
// To run Maven on a Windows agent, use
bat "mvn -Dmaven.test.failure.ignore=true clean package"
}
post {
// If Maven was able to run the tests, even if some of the test
// failed, record the test results and archive the jar file.
success {
junit '**/target/surefire-reports/TEST-*.xml'
archiveArtifacts 'target/*.jar'
}
}
}
stage('Code Analysis') {
steps {
withSonarQubeEnv('Sonarqube 8.5 Local') {
bat 'mvn clean package sonar:sonar'
}
}
}
}
}
