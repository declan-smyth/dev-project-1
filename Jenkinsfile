pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        echo 'Message: Checkout'
        git(url: 'https://github.com/declan-smyth/dev-project-1.git', branch: 'master')
      }
    }

    stage('Build Application'){
      steps {
          bat "\"${tool 'MSBuild'}\" ds-core-website.sln /p:Configuration=Release /p:Platform=\"Any CPU\" /p:ProductVersion=1.0.0.${env.BUILD_NUMBER}"
      }
    }
  }
  environment {
    Version = '10'
  }
}