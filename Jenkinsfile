pipeline {
  environment {
    registry = "lokeswar28/docker_image_using_jenkinsfile"
    registryCredential = "dockerhub"
    dockerImage = ''
  }
  agent any
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
  }
