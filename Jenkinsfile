pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git branch:"master", url:'https://github.com/dawnslawter/simple-node-js-react-npm-app.git'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'Default'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}
