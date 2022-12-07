pipeline {
  environment {
    registry = "dlfarande/dockerhubregistry"
    registryCredential = 'dockerhubedentials'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Checkout') {
      steps {
        git credentialsId: 'githubcredentials', url: 'https://github.com/dlfarande/Devops_project.git'
      }
    }
    stage('Docker Build') {
      steps{
        script {
          dockerImage = docker.build registry + ":latests-$BUILD_NUMBER"
        }
      }
    }
    stage('Docker Push') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
           dockerImage.push()
          }
        }
      }
    }
  }
}

