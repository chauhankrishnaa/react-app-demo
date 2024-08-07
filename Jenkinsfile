pipeline {
    agent {
        label 'agent1'
    }

    environment {
        NODE_HOME = '/usr/bin/node'
        PATH = "$NODE_HOME/bin:$PATH"
    }

    stages {

  

        stage("Cleanup the workspace"){
            steps{
                cleanWs()
            }

        }

        
    stage('Checkout') {
            steps {
                // Pull the code from GitHub
                // git branch: 'main', credentialsId: 'github-react-credentials', url: 'https://github.com/chauhankrishnaa/react-app-demo.git'
                checkout scm
            }
        }
        
        stage('Install dependencies') {
            steps {
                // Install Node.js dependencies
                sh 'npm install'
            }
        }
         stage('Build the code') {
            steps { 
                // Build React.js application
                sh 'npm run build'
            //repo
            }   
         }
         stage('start') {
            steps { 
                // Build React.js application
                sh 'npm run start&'
            }
        
}
}
     post {
         always {
             echo 'This will always run'
         }
         success {
             echo 'This will run only if successful'
             mail bcc: '', body: "<br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: 'krishna.chauhan@acuteinformatics.in', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "Sucsses: Project name ${env.JOB_NAME}", to: "krishna.chauhan@acuteinformatics.in";
         }
         failure {
             echo 'This will run only if Pipeline Failed'
             // Sending an email notification with details about the failure
             mail bcc: '', body: "<b>Example</b><br>Project: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> URL de build: ${env.BUILD_URL}", cc: 'krishna.chauhan@acuteinformatics.in', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "ERROR CI: Project name -> ${env.JOB_NAME}", to: "krishna.chauhan@acuteinformatics.in";
         }
         unstable {
             echo 'This will run only if the run was marked as unstable'
         }