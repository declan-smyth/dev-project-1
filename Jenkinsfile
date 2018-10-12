pipeline {
  agent {
    node {
      label 'windows'
    }

  }
  stages {
    stage('Build Application') {
      steps {
        bat "\"${tool 'MSBuild'}\" ds-core-website.sln /p:Configuration=Release /p:Platform=\"Any CPU\" /p:ProductVersion=1.0.0.${env.BUILD_NUMBER}"
      }
    }
  }
  environment {
    Version = '10'
  }
}