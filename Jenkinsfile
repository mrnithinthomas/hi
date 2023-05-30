pipeline {
    agent any

    stages {
        stage('Check Port Availability') {
            steps {
                script {
                    def port = 8080 // Change the port number as per your requirement

                    def isPortAvailable = checkPortAvailability(port)
                    if (isPortAvailable) {
                        echo "Port ${port} is available"
                    } else {
                        echo "Port ${port} is not available"
                    }
                }
            }
        }
    }
}

def checkPortAvailability(port) {
    def socket = new java.net.Socket()
    def isPortAvailable = true

    try {
        socket.bind(new InetSocketAddress("localhost", port))
    } catch (BindException e) {
        isPortAvailable = false
    } finally {
        socket.close()
    }

    return isPortAvailable
}
