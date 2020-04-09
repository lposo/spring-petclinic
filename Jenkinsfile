pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh './mvnw clean' 
            }
        }
        stage ('Test') {
            steps{
                sh './mvnw test'
            }
        }
        stage ('Package'){
            steps{
                sh './mvnw package'
            }
        }
        stage ('Deploy'){
            when{
                branch 'master'
            }
            steps{
                sh './mvnw deploy'
            }
        }
    }
    post {
        success {
          slackSend (color: '#00FF00', message: "SUCCESSFUL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
        }
    }
}
