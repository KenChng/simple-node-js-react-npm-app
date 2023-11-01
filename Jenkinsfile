pipeline {
    agent {
        docker {
            image 'node:18.18.0-alpine3.18' 
            args '-p 3000:3000' 
        }
    }
    stages {
	stage('OWASP Dependency-Check Vulnerabilities') {
	      steps {
	        dependencyCheck additionalArguments: ''' 
	                    -o './'
	                    -s './'
	                    -f 'ALL' 
	                    --prettyPrint''', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'
	        
	        dependencyCheckPublisher pattern: 'dependency-check-report.xml'
	      }
	}
    }   
}
