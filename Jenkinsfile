//Declarative approach

pipeline {
  agent any
  
  //agent {docker {image 'maven:3.6.3'} }
  environment {
	dockerHome = tool 'myDocker'
	mavenHome = tool 'myMaven'
	PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
  }

  stages {
    stage('checkout') {
      steps {
        sh 'mvn --version'
		sh 'docker version'
		echo "Build"
		echo "PATH - $env.PATH"
		echo "BUILD_NUMBER - $env.BUILD_NUMBER"
		echo "BUILD_ID - $env.BUILD_ID"
		echo "BUILD_TAG - $env.BUILD_TAG"
		echo "BUILD_URL - $env.BUILD_URL"	
		echo "JOB_NAME - $env.JOB_NAME"
      }
    }
    stage ('Compile') {
	 steps {
		sh "mvn clean compile"
	 } 

    }

    stage('Test') {
      steps {
        sh "mvn test"
      }
    }

    stage('Integration') {
      steps {
        sh "mvn failsafe:Integration-Test failsafe:verify"
      }
    } 

  }
	post {
		success {
			echo 'Code executed successfully'
		}
		failure {
			echo 'Code execution failed'
		}
	}
}