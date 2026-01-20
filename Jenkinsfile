pipeline {
  agent any

  stages {

    stage('Checkout Code') {
      steps {
        git branch: 'main', url: 'https://github.com/shivakumarreddy6740/CI-CD-demo.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        bat 'docker build -t oshivakumarreddy/order:1.0 .'
      }
    }

    stage('Docker Login & Push') {
      steps {
        withCredentials([usernamePassword(
          credentialsId: 'dockerhub-creds',
          usernameVariable: 'DOCKER_USER',
          passwordVariable: 'DOCKER_PASS'
        )]) {
          bat '''
            docker login -u %DOCKER_USER% -p %DOCKER_PASS%
            docker push oshivakumarreddy/order:1.0
          '''
        }
      }
    }

    stage('Deploy to Kubernetes') {
      steps {
        bat 'kubectl apply -f deployment.yaml'
      }
    }
  }
}
