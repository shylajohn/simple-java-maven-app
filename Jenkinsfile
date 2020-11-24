pipeline {
    agent any
    
    stages {
        stage('build') {
            steps {
                slackSend (color: '#FFFF00', message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
                emailext body: 'A Test EMail', recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']], subject: 'Test'

                sh 'mvn --version'
                //slackSend channel: 'devops', color: '#439FE0', message: 'successful build', teamDomain: 'shyla-company', tokenCredentialId: 'slack-secret'
                //slackSend (color: '#FFFF00', message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})"   
            }
        }
        stage('post-build') {
            steps {
                slackSend (color: '#FFFF00', message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
                sh 'printenv'

                
            }
        }
    }
    
     post {
       // only triggered when blue or green sign
       success {
           slackSend (color: '#FFFF00', message: "success")
       }
       // triggered when red sign
       failure {
           slackSend (color: '#FFFF00', message: "failure")
       }
       // trigger every-works
    }
}
