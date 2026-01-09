//Declarative approach

pipeline {
  //agent any
  
  agent {docker {image 'maven:3.6.3'} }

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

    stage('Integration') {
      steps {
        echo "Integration"
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