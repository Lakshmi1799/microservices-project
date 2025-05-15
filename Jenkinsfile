pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-sravanthi1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://CA481D72B9E7BC8A89DF78C2C60B4C07.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-sravanthi1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://CA481D72B9E7BC8A89DF78C2C60B4C07.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
