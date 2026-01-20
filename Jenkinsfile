pipeline {
  agent any

  stages {

    stage('Checkout Code') {
      steps {
        git 'https://github.com/shivakumarreddy6740/CI-CD-demo.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        bat 'docker build -t oshivakumarreddy/order:1.0 .'
      }
    }

    stage('Push Image') {
      steps {
        bat 'docker push oshivakumarreddy/order:1.0'
      }
    }

    stage('Deploy to Kubernetes') {
      steps {
        bat 'kubectl apply -f deployment.yaml'
      }
    }
  }
}
