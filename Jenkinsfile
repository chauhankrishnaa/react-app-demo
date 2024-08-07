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
            emailext (
                subject: 'Build Notification',
                body: 'The build is complete.',
                to: 'krishna.chauhan@acuteinformatics.in',
                cc: 'krishna.chauhan@acuteinformatics.in' 'jaid.shaikh@acuteinformatics.in',
                attachmentsPattern: '**/*.log'
            )
        }
	}
    //  post {
    //      always {
    //          echo 'This will always run'
    //      }
    //      success {
    //         //  echo 'This will run only if successful'
    //         //  mail bcc: '', body: "<br>Project Name: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> Build URL: ${env.BUILD_URL}", cc: 'krishna.chauhan@acuteinformatics.in', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "Sucsses: Project Name: ${env.JOB_NAME}", to: "krishna.chauhan@acuteinformatics.in";
    //      }
    //      failure {
    //          echo 'This will run only if Pipeline Failed'
    //          // Sending an email notification with details about the failure
    //          mail bcc: '', body: "<br>Project Name: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> Build URL: ${env.BUILD_URL}", cc: 'krishna.chauhan@acuteinformatics.in', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "ERROR CI: Project Name: ${env.JOB_NAME}", to: "krishna.chauhan@acuteinformatics.in";
    //      }
    //      unstable {
    //          echo 'This will run only if the run was marked as unstable'
    //      }
    //     }
}