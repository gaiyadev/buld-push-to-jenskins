pipeline {
  agent any

  tools {
    nodejs 'NodeJS'
  }

  environment {
    NODE_ENV = 'development'
    IMAGE_NAME = 'my-app' // your image name here
  }

  stages {
    stage('Clone Repository') {
      steps {
        checkout scm
      }
    }

    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }

    // stage('Deploy') {
    //   steps {
    //     script {
    //       withCredentials([usernamePassword(credentialsId: 'dockerhub-creds', usernameVariable: 'DOCKER_USERNAME', passwordVariable: 'DOCKER_PASSWORD')]) {
    //         docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-creds') {
    //           def customImage = docker.build("${DOCKER_USERNAME}/${env.IMAGE_NAME}:latest")
    //           customImage.push()
    //         }
    //       }
    //     }
    //   }
    // }
  }

  post {
    success {
      echo 'Pipeline executed successfully.'
    }
    failure {
      echo 'Pipeline failed.'
    }
  }
}
