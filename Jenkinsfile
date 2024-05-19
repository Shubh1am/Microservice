pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes', contextName: '', credentialsId: 'k8-cred', namespace: 'webapps', serverUrl: 'https://172.31.40.195:6443']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes', contextName: '', credentialsId: 'k8-cred', namespace: 'webapps', serverUrl: 'https://172.31.40.195:6443']]) {
                    sh "kubectl get svc -webapps"
                    
                }
            }
        }  
    }
}
