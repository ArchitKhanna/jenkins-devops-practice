pipeline {
	//agent any
	agent { dockerNode { image 'maven:3.6.3'} }
	stages {
		stage('Build') {
			steps {
				sh 'mvn --version'
				echo "Build"
			}
		}
		stage('Test') {
			steps {
				echo "Test"
			}
		}
		stage('Integration Test') {
			steps {
				echo "Integration Test"
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
