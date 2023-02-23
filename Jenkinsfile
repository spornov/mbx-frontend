pipeline {
  agent any
  tools {
    nodejs '14.16.0'
  }
  stages {
    stage('Build') {
      steps {
        script {
          try {
            sh 'ls -a'
          } catch(err) {
            throw err;
          }
        }
      }
    }
    stage('Deploy') {
      steps {
        script {
          try {
            withCredentials([sshUserPrivateKey(credentialsId: '35.159.30.64', keyFileVariable: 'keyFile', usernameVariable: 'userName')]) {
              def remote = [name: 'hometest', host: '35.159.30.64', user: 'userName', allowAnyHosts: true]
              sshCommand remote: remote, command: "ls -lrt"
            }
          } catch (err) {
            throw err
          }
        }
      }
    }
  }
}
