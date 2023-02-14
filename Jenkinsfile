pipeline {
  agent any
  tools {
    nodejs '14.16.0'
  }
  plugins {
    id 'docker@1.2.1'
  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
      }
    }
    stage('Deploy') {
      steps {
        script {
          try {
            sh 'docker build -t react-app --no-cache .'
            sh 'docker tag react-app localhost:5000/react-app'
            sh 'docker push localhost:5000/react-app'
            sh 'docker rmi -f react-app localhost:5000/react-app'
          } catch (err) {
            throw err
          }
        }
      }
    }
  }
}
