pipeline {
    agent any
    
    stages {
        stage('Check Port Availability') {
            steps {
                script {
                    def port = 8080  // Replace with your desired port number
                    
                    def isPortAvailable = checkPortAvailability(port)
                    
                    if (isPortAvailable) {
                        println "Port ${port} is available."
                    } else {
                        println "Port ${port} is not available."
                    }
                }
            }
        }
    }
}

def checkPortAvailability(port) {
    def cmd = "bash -c 'echo \"\" > /dev/tcp/localhost/${port}'"
    def proc = cmd.execute()
    proc.waitFor()
    
    return proc.exitValue() == 0
}

