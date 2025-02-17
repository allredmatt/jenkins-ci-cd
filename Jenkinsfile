pipeline {
	agent any 
	stages {
		stage('Build') {
			steps {
				echo 'Build'
			}
		}
		stage('Test') {
			steps {
				echo 'Test'
			}
		}
		stage('Integration') {
			steps {
				echo 'Integration'
			}
		}
	}
	post {
		always {
			echo 'I always run'
		}
		success {
			echo 'I run if successful'
		}
		failure {
			echo 'I failed to build'
		}
	}
}
