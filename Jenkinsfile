pipeline {
    agent any
    
    stages {
        stage('Check and Delete Pod') {
            steps {
                script {
                  
                 		withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: '', contextName: '', credentialsId: 'kubesecretfile', namespace: '', serverUrl: '']])
                    {
                    def podName = 'projectx-pod'  // Replace with your pod name
                    
                    // Check if the pod exists
                    def podExists = sh(returnStdout: true, script: "kubectl get pod ${podName} --ignore-not-found=true").trim()
                    
                    if (podExists) {
                        // Delete the pod if it exists
                        sh "kubectl delete pod ${podName}"
                        sh "kubectl apply -f manifest.yml"
                    } else {
                        // Create a new pod if it doesn't exist
                        sh "kubectl apply -f manifest.yml"  // Replace with your pod creation command
                    }
                    }
                }
            }
        }
    }
}
