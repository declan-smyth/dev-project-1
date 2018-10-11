pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        echo 'Message: Checkout'
        git(url: 'https://github.com/declan-smyth/dev-project-1.git', branch: 'master')
      }
    }
  }
  environment {
    Version = '10'
  }
}