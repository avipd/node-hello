pipeline {
  agent {
    node {
      label 'Docker'
    }

  }
  stages {
    stage('CeckoutCode') {
      steps {
        git(url: 'https://github.com/avipd/node-hello.git', branch: 'master', changelog: true, poll: true)
      }
    }

    stage('Build DockerFile') {
      steps {
        sh 'docker build . -t node-helow:$BUILD_ID'
      }
    }

  }
}