pipeline {
	//agent any
	agent {
		docker {
			//image 'maven:3.6.3'
			image 'node:21.7'
		}
	} 
	stages {
		stage('Build') {
			steps {
				echo 'Build'
				//sh 'mvn --version'
				sh 'node --version'
			}
			post {
				always{
					echo 'I run at the end of the build stage'
				}
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
