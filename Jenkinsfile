//Declarative approach

pipeline {
  agent {
    docker {
      image 'maven:3.6.3-jdk-8'
      // only needed if you also run docker commands (optional)
      args '-v /var/run/docker.sock:/var/run/docker.sock'
    }
  }

  stages {
    stage('checkout') {
      steps {
        checkout scm
        sh 'java -version'
        sh 'mvn -version'
        // docker version will work only if socket is mounted and docker exists in container
        // sh 'docker version'
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

    stage('Integration') {
      steps {
        sh 'mvn failsafe:integration-test failsafe:verify'
      }
    }
  }

  post {
    success { echo 'Code executed successfully' }
    failure { echo 'Code execution failed' }
  }
}