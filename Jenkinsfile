pipeline {
    agent {
        docker {
            image 'node:18.18.0-alpine3.18' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
	stage('Test'){
	    steps{
	        sh './jenkins/scripts/test.sh'
	    }
	}
	stage('Deliver'){
	    steps{
	        sh './jenkins/scripts/deliver.sh'
		input message: 'Finished using the website? (Click "proceed" to continue)'
		sh './jekins/scripts/kill.sh'
	    }
	}
    }
}
