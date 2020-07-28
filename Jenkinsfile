node {
  environment {
       PATH = "$PATH:/usr/local/bin"
  }

   try {   
     stage('Checkout') {
      checkout scm
      }
      stage('Environment') {
        sh 'git --version'
        echo "Branch: ${env.BRANCH_NAME}"
        sh 'docker -v'
        sh '/usr/local/bin/docker-compose -v'
        sh 'printenv'
      }
      // stage('Build Docker image') {
      //   sh 'docker-compose build'
        // sh "/usr/bin/docker-compose build"
      // }
      // stage('Deployment...') {
      //   sh 'docker-compose up -d'
      // }
    }
   catch (err) {
    throw err
  }
 }
