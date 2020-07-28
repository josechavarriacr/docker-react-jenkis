pipeline {
  environment {
    PATH = "$PATH:/usr/local/bin"
  }
 node {
   try {
     stage('Checkout') {
      checkout scm
    }
    stage('Environment') {
      sh 'git --version'
      echo "Branch: ${env.BRANCH_NAME}"
      sh 'docker -v'
      sh 'printenv'
    }
    stage('Build Docker image') {
      sh 'docker-compose build'
    }
    stage('Deployment...') {
      sh 'docker-compose up -d'
    }
   }
   catch (err) {
    throw err
  }
 }
}