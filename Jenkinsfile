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
    // stage('Build Docker test'){
    //  sh 'docker build -t react-test -f web/Dockerfile.test --no-cache .'
    // }
    // stage('Docker test'){
    //   sh 'docker run --rm react-test'
    // }
    // stage('Clean Docker test'){
    //   sh 'docker rmi react-test'
    // }

    stage("Build and start test image") {
        steps {
            sh "docker-composer build"
            sh "docker-compose up -d"
            waitUntilServicesReady
        }
    }
    // stage('Deploy'){
    //   if(env.BRANCH_NAME == 'master'){
    //     sh 'docker build -t react-test -f web/Dockerfile --no-cache .'
    //     sh 'docker tag react-app localhost:5000/react-app'
    //     sh 'docker push localhost:5000/react-app'
    //     sh 'docker rmi -f react-app localhost:5000/react-app'
    //   }
    // }
  }
  catch (err) {
    throw err
  }
}



