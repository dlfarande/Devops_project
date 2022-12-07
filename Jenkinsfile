pipeline {
  environment {
    registry = "nileshkardile831/incedo"
    registryCredential = 'dockercredentials'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Checkout') {
      steps {
        git credentialsId: '777a7344-89b9-4515-9830-3bd6e9a66158', url: 'https://github.com/nileshkardile831/incedo-repo.git'
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

