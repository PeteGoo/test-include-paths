pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        script {
          node { 
            checkout scm

             def customImage = docker.build("my-image-3:${env.BUILD_ID}")
          }
        }

       }
    }
  }
}