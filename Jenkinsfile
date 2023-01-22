pipeline {
  agent any
  stages {
    stage('Chekout Code') {
      steps {
        git(url: 'https://github.com/Akorstudio/React-Express-forScramjet', branch: 'dev')
      }
    }

    stage('Log') {
      steps {
        sh 'ls -la'
      }
    }

    stage('Build-Server') {
      steps {
        sh 'docker build --rm -t re-server-dev -f ./server/Dockerfile.dev ./server'
      }
    }

  }
}