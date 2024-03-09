pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    // Compile the .cpp file using a shell script
                    sh 'g++ -o output_file sample.cpp'
                }
            }
            post {
                failure {
                    echo 'Build failed: pipeline failed'
                }
            }
        }
        
        stage('Test') {
            steps {
                script {
                    // Print the output of the .cpp file using a shell script
                    sh './output_file'
                }
            }
            post {
                failure {
                    echo 'Test failed: pipeline failed'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                // Add deployment steps
                script {
                    // Example: Copy output_file to a remote server using SCP
                    sh 'scp output_file user@remote-server:/path/to/deploy'
                    
                    // Example: Restart the application on the remote server using SSH
                    sh 'ssh user@remote-server "sudo systemctl restart myapp"'
                }
            }
        }
    }
    
    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}
