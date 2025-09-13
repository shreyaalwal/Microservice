pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '',
                    clusterName: 'EKS-3',
                    contextName: '',
                    credentialsId: 'k8-token',
                    namespace: 'webapps',
                    serverUrl: 'https://3F1EFBF3B9E2CF2EE5DA9C581113CCB0.gr7.ap-south-1.eks.amazonaws.com'
                ]]) {
                    sh "kubectl apply -f deployment-service.yml"
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[
                    caCertificate: '',
                    clusterName: 'EKS-3',
                    contextName: '',
                    credentialsId: 'k8-token',
                    namespace: 'webapps',
                    serverUrl: 'https://3F1EFBF3B9E2CF2EE5DA9C581113CCB0.gr7.ap-south-1.eks.amazonaws.com'
                ]]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
