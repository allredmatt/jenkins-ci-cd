pipeline {
	agent any
	// agent {
	// 	docker {
	// 		//image 'maven:3.6.3'
	// 		image 'node:21.7'
	// 	}
	//} 
	stages {
		stage('Build') {
			steps {
				//sh 'mvn --version'
				// sh 'node --version'
				echo 'Build'
				echo "Path: $PATH"
				echo "Build: Number: $env.BUILD_NUMBER"
				echo "Build ID: $env.BUILD_ID"
				echo "Build Tag: $env.BUILD_TAG"
				echo "Build URL: $env.BUILD_URL"
				echo "Job Name: $env.JOB_NAME"
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
