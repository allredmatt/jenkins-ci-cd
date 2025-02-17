pipeline {
	agent any
	environment {
		dockerHome = tool "myDocker"
		mavenHome = tool "myMaven"
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"

	}
	// agent {
	// 	docker {
	// 		//image 'maven:3.6.3'
	// 		image 'node:21.7'
	// 	}
	//} 
	stages {
		stage('Checkout') {
			steps {
				sh 'mvn --version'
				sh 'docker --version'
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
		stage('Compile') {
			steps {
				sh "mvn clean compile -e"
			}
		}
		stage('Test') {
			steps {
				sh "mvn test"
			}
		}
		stage('Integration') {
			steps {
				echo 'Integration'
			}
		}
		stages('Package') {
			steps {
				sh "mvn package -DskipTests"
			}
		}

		stage('Build Docker Image') {
			steps{
				//docker build -t allredmatt/currency-exchange-devops:$env.BUILD_TAG
				script {
					dockerImage = docker.build("allredmatt/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}
		}
		stage('Push docker Image') {
			steps {
				script {
					docker.withRegistry('', 'docker-hub-credentials') {
						dockerImage.push()
						dockerImage.push('latest')
					}
				}
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
