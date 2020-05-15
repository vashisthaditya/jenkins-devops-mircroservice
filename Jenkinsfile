pipeline {
	agent any
	//agent {docker {image 'maven:3.6.3'}}
	environments {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {
		stage('Checkout') {
			steps
			{
				sh 'mvn --version'
				sh 'docker version'
				echo "BUILD"
				echo "PATH - $PATH"
				echo "BUILD NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
				
			}

		}
		stage('Compile') {
			steps{
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
				echo "mvn failsafe:integration-test failsafe:verify"
			}
		}
	}
post {
	always {
		echo 'Im awesome. I run always'
	}
	success {
		echo 'I run when you are successful'

	}
	failure {
		echo 'I run when you fail'
	}
}	
			
}
