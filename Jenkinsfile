pipeline {
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

    stage('Docker Build') {
      steps {
        sh '''docker build -t agomezjr94/flask app .
'''
      }
    }

    stage('Docker Login') {
      steps {
        sh 'docker login -u agomezjr94 -p dckr_pat_4vsgyJubZvGGKo0QI0GewPS7kuE'
      }
    }

    stage('Docker Push') {
      steps {
        sh 'docker push agomezjr94/flask_app'
      }
    }

  }
}