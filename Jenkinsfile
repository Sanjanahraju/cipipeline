pipeline {
agent any
stages {
stage('Checkout')
{ steps {
// Check out code from Git repository

git url: 'https://github.com/Sanjanahraju/cipipeline.git', branch: 'main'

}
}
stage('Build')
{ steps {
script{
def mvnHome = tool 'Maven-3.8.7'
sh "${mvnHome}/bin/mvn clean package"
}
}
}
stage('Test') {
steps {
// Optionally, separate test execution if needed
sh 'mvn test'
}
}
}
post {
always {
// Archive test reports
junit '**/target/surefire-reports/*.xml'
}
success {
echo 'Build and tests succeeded!'
}
failure {
echo 'Build or tests failed.'
}
}
}
