pipeline {
  agent any
  stages {
    stage ('Building the docker image') {
      steps {
        sh "docker build -t jenkinstraining.azurecr.io/first-sample-docker-image-66454:$BUILD_NUMBER ."
      }
    }
    stage ('Docker image push to docker registry') {
      environment {
        DOCKER_CONFIG = credentials('jenkins-training-docker-config-json')
      }
      steps {
        sh "export DOCKER_CONFIG=\"\$(dirname \"\$DOCKER_CONFIG\")\"; docker push jenkinstraining.azurecr.io/first-sample-docker-image-66454:$BUILD_NUMBER"
      }
    }
  }
}
