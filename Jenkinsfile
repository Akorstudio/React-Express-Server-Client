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

    stage('Build') {
      steps {
        sh 'docker-compose -f docker-compose.dev.yml up --build'
      }
    }

  }
}