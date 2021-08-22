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

    stage('Push Docker Image') {
      steps {
        withDockerRegistry(credentialsId: 'docker-hub-cred', url: 'https://index.docker.io/v1/') {
          sh '''docker tag node-helow:$BUILD_ID aviperets/node-hello:$BUILD_ID && docker push aviperets/node-hello:$BUILD_ID '''
    
        
        }
      }
    }

  }
}
