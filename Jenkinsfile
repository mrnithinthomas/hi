pipeline {
    agent any
    
    stages {
        stage('Check and Delete Pod') {
            steps {
                script {
                    def podName = 'projectx-pod'  // Replace with your pod name
                    
                    // Check if the pod exists
                    def podExists = sh(returnStdout: true, script: "kubectl get pod ${podName} --ignore-not-found=true").trim()
                    
                    if (podExists) {
                        // Delete the pod if it exists
                        sh "kubectl delete pod ${podName}"
                    } else {
                        // Create a new pod if it doesn't exist
                        sh "kubectl create pod your-pod-creation-command"  // Replace with your pod creation command
                    }
                }
            }
        }
    }
}