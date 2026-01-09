//Declarative approach

pipeline {
  agent any

  stages {
    stage('Build') {
      steps {
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