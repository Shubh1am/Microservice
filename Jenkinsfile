pipeline {
    agent any

    stages {
        stage('Build and Test') {
            steps {
                sh 'gradle test' // Replace with your build and test command (e.g., npm test, gradle test)
            }
        }
        stage('OWASP Dependency Check') {
            steps {
                sh 'mvn dependency:check -DskipTests' // Replace with your OWASP dependency checker command
            }
        }
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker build -t shubhammutkalwar/adservice:latest ."
                    }
                }
            }
        }
        stage('Trivy Scan') {
            steps {
                script {
                    def imageName = "your-image-name:latest" // Replace with your image name and tag
                    sh "trivy image --format json --severity CRITICAL,HIGH $imageName > trivy-report.json"
                    // You can archive the report or send it for further analysis
                }
            }
        }        
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                        sh "docker push shubhammutkalwar/adservice:latest "
                    }
                }
            }
        }
    }
}
