pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                bat 'gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            }
        }
    stage('Build Docker Image') {
when{
branch 'ajithrp02'
}
steps{
scripts{
app= docker.build("ajithrp02/train-schedule")

}
}
}
stage('Push Docker image'){
when {
branch 'ajithrp02'
}
steps{
script{
docker.withRegistry('https://registry.hub.docker.com','docker_hub_login'){
	app.push("${env.BUILD_NUMBER}")
app.push("Latest")
}
}
}
}
}
}   
