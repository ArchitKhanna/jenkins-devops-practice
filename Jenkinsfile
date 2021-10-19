pipeline {
	agent any

	environment {
		dockerHome = tool 'my-docker'
		mavenHome = tool 'my-maven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}

	stages {
		stage('Checkout') {
			steps {
				echo "Build"
				sh 'mvn --version'
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Compile') {
			steps {
				sh 'mvn clean compile'
			}
		} 
		stage('Test') {
			steps {
				sh 'mvn test'
			}
		}
		stage('Integration Test') {
			steps {
				sh 'mvn failsafe:integration-test failsafe:verify'
			}
		}
	} 
	post {
		always {
			echo 'Run Always'
		}
		success {
			echo 'Run Successfully'
		}
		failure {
			echo 'Run Failure'
		}
		//changed (changed status compared to previous run) or unstable (Build succeeded but test failed)
	}
}
