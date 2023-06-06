pipeline {

environment{
  registry = "agomezjr94/flask_app"
  registryCredentials = "agomezjr94"
  cluster_name = "skillstorm"
}

  agent {
    node {
      label 'docker'
    }

  }
  stages {
    stage('Git') {
      steps {
        git(url: 'https://github.com/agomez94/flasking.git', branch: 'main')
      }
    }

  stage('Build Stage'){
    steps {
      script {
        dockerImage = docker.build(registry)
      }
    }
  }

  stage('Deployment Stage') {
    steps{
      script {
        docker.withRegistry('', registryCredentials) {
          dockerImage.push()
        }
      }
    }
  }

  }
}