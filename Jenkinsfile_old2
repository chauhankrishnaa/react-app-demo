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
                git branch: 'main', credentialsId: 'github-react-credentials', url: 'https://github.com/chauhankrishnaa/react-app-demo.git'
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
         stage('Archive Artifact'){
		    steps{
		        archiveArtifacts artifacts:'target/*.war'
		}
	}
         stage('start') {
            steps { 
                // Build React.js application
                sh 'npm run start&'
            }
        
}
}
    }
