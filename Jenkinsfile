pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'secret', namespace: 'singam', serverUrl: 'https://3A8CFCEF808E8CEA6B683EC07CDCD998.gr7.ap-south-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'secret', namespace: 'singam', serverUrl: 'https://3A8CFCEF808E8CEA6B683EC07CDCD998.gr7.ap-south-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n singam"
                }
            }
        }
    }
}
