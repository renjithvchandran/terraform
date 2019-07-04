pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('checkout') {
      steps {
        checkout scm
        sh 'mkdir -p myterraform'
        sh 'echo $GOOGLE_CREDENTIALS > keyfile.json'
        sh 'cat keyfile.json'
      }
    }
    stage('plan') {
      steps {
        sh 'pwd'
        sh 'terraform init'
        sh 'terraform plan -out myplan'
      }
    }
  }
  environment {
    GOOGLE_CREDENTIALS = credentials('GCP-USER')
  }
}
