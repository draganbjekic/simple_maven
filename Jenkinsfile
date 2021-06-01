pipeline {
    agent any
    stages{
        stage('build'){
            steps {
                sh 'mvn clean install'
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml'
                }
            }
        }
    }
    post {
        always {
            mail to :"bjekic.beograd@yahoo.com",
                subject: "New build report: ${currentBuild.fullDisplayName}",
                body:"Check out status at ${env.BUILD_URL}"
        }
    }
}