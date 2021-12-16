pipeline {
  agent any
  stages {
    stage ('Build docker image') {
      steps {
        sh "docker build -t jenkinstraining.azurecr.io/first-sample-docker-image-66454:$BUILD_NUMBER ."
      }
    }
    stage ('Push docker image to container registry') {
      environment {
        DOCKER_CONFIG = credentials('jenkins-training-docker-config-json')
      }
      steps {
        sh "export DOCKER_CONFIG=\"\$(dirname \"\$DOCKER_CONFIG\")\"; docker push jenkinstraining.azurecr.io/first-sample-docker-image-66454:$BUILD_NUMBER"
      }
    }
  }
}
