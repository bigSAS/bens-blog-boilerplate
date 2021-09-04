pipeline {
  agent {
    node {
      label 'boxd'
    }
  }

  environment {
    DOCKER_USER = credentials('DOCKER_USER')
    DOCKER_TOKEN = credentials('DOCKER_TOKEN')
  }

  stages {
    
    stage('Docker login') {
      sh "docker login -u ${DOCKER_USER} -p ${DOCKER_TOKEN} docker.io"
    }

    stage('Build docker image') {
      steps {
        // todo: IMG_TAG - tag from repo pass to build
        sh "docker-compose build"
      }
    }

    stage('Push docker image') {
      steps {
        sh "docker-compose push app"
      }
    }
  }
}
