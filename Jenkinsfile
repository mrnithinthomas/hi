pipeline {
    agent any

    stages {
        stage('Check Port Availability') {
            steps {
                script {
                    def port = 8080  // Replace with the desired port number

                    try {
                        sh "lsof -i :${port}"
                        echo "Port ${port} is available"
                    } catch (Exception e) {
                        echo "Port ${port} is not available"
                        // Perform actions with admin permissions
                    }
                }
            }
        }
    }
}
