pipeline {
    properties([parameters([string(defaultValue: 'http://169.254.169.254/latest', description: '', name: 'metadata', trim: false)])])
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            }
        }
    }
    stage('build docker image'){
        when {
            branch 'master'
        }
        steps{
            scripts{
                app = docker.build("devopsmeet2019/meet")
                app.inside{
                    sh 'echo curl $9localhost:8080)'
                }
            }
        }      
}
