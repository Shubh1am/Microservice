pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes', contextName: '', credentialsId: 'k8-cred', namespace: 'webapps', serverUrl: 'k8-ip']]) {
                    sh "kubectl apply -f deployment-service.yml"              
                }
            }
        }
        stage('view services') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'kubernetes', contextName: '', credentialsId: 'k8-cred', namespace: 'webapps', serverUrl: 'k8-ip']]) {
                    sh "kubectl get svc -n webapps"        
                }
            }
        }  
     }
}

