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

    stage('Build apps') {
      parallel {
        stage('Build-Server') {
          steps {
            sh 'docker build -t re-server-dev -f ./server/Dockerfile.dev ./server'
          }
        }

        stage('Build-Client') {
          steps {
            sh 'docker build --rm -t re-client-dev -f ./client/Dockerfile.dev ./client'
          }
        }

      }
    }

    stage('Log into DHub') {
      environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
      }
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }

    stage('Push server-dev') {
      steps {
        sh 'docker push alexgk/re-server-dev:latest'
      }
    }

  }
}