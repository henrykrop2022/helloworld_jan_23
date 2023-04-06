pipeline {
  agent any

  environment {
    KUBECONFIG = '/path/to/your/kubeconfig'
  }

  stages {
    stage('Check connectivity') {
      steps {
        withKubeConfig(credentialsId: 'eks_credential', kubeconfigFileVariable: 'KUBECONFIG') {
          sh 'kubectl get nodes'
        }
      }
    }

    stage('Deploy') {
      steps {
        withKubeConfig(credentialsId: 'eks_credential', kubeconfigFileVariable: 'KUBECONFIG') {
          sh 'kubectl apply -f deployment.yaml'
        }
      }
    }
  }
}
