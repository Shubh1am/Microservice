pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes', contextName: '', credentialsId: 'k8-cred', namespace: 'webapps', serverUrl: 'https://172.31.0.249:6443/']]) {
                    sh "kubectl apply -f deployment-service.yml"              
                }
            }
        }
        stage('view services') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes', contextName: '', credentialsId: 'k8-cred', namespace: 'webapps', serverUrl: 'https://172.31.0.249:6443/']]) {
                    sh "kubectl get svc -n webapps"        
                }
            }
        }  
     }
}

