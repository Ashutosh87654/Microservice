pipeline{
    agent any
    stages{
        stage("Deploy To Kubernetes"){
            steps{
                withKubeConfig(caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://FA919B3B6EF7FC556C2C701DF610C9C1.gr7.ap-south-1.eks.amazonaws.com') {
                sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        stage("verify Deployment"){
            steps{
                withKubeConfig(caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://FA919B3B6EF7FC556C2C701DF610C9C1.gr7.ap-south-1.eks.amazonaws.com') {
                sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
