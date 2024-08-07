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
            //  echo 'This will run only if successful'
            //  mail bcc: '', body: "<br>Project Name: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> Build URL: ${env.BUILD_URL}", cc: 'krishna.chauhan@acuteinformatics.in', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "Sucsses: Project Name: ${env.JOB_NAME}", to: "krishna.chauhan@acuteinformatics.in";
             mail bcc: 'jaid.shaikh@acuteinformatics.in', body: "
<head>
    <style>
        body {
            font-family: Arial, sans-serif;
            color: #333333;
        }
        .header {
            background-color: #f2f2f2;
            padding: 10px;
        }
        .content {
            margin: 20px;
        }
        .footer {
            margin-top: 20px;
            font-size: 12px;
            color: #777777;
        }
        .status-success {
            color: green;
        }
        .status-failure {
            color: red;
        }
    </style>
</head>
<body>
    <div class="header">
        <h2>Build Notification</h2>
    </div>
    <div class="content">
        <p>Job Name: <strong>${PROJECT_NAME}</strong></p>
        <p>Build Number: <strong>${BUILD_NUMBER}</strong></p>
        <p>Build Status: <strong class="status-${BUILD_STATUS,lower}">${BUILD_STATUS}</strong></p>
        <p>Build URL: <a href="${BUILD_URL}">${BUILD_URL}</a></p>
        <hr>
        <h3>Changes:</h3>
        <ul>
            $CHANGES
        </ul>
        <h3>Build Log:</h3>
        <pre>$BUILD_LOG</pre>
    </div>
    <div class="footer">
        <p>This is an automated message from Jenkins. Please do not reply to this email.</p>
    </div>
</body>
</html>
", cc: 'krishna.chauhan@acuteinformatics.in', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "ERROR CI: Project Name: ${env.JOB_NAME}", to: "krishna.chauhan@acuteinformatics.in";

         }
         failure {
             echo 'This will run only if Pipeline Failed'
             // Sending an email notification with details about the failure
             mail bcc: '', body: "<br>Project Name: ${env.JOB_NAME} <br>Build Number: ${env.BUILD_NUMBER} <br> Build URL: ${env.BUILD_URL}", cc: 'krishna.chauhan@acuteinformatics.in', charset: 'UTF-8', from: '', mimeType: 'text/html', replyTo: '', subject: "ERROR CI: Project Name: ${env.JOB_NAME}", to: "krishna.chauhan@acuteinformatics.in";
         }
         unstable {
             echo 'This will run only if the run was marked as unstable'
         }
        }
}