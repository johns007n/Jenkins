node {
def app
stage('Clone repository') {

checkout scm
}
stage('Build image') {

app = docker.build("johnsonniti/sample:v1")
}
stage('Test image') {
app.inside {

sh 'echo "PASS"'
}
}
stage('Push image') {
docker.withRegistry('https://docker.io') {
app.push("${env.BUILD_NUMBER}")
app.push("latest")
}
}
}
