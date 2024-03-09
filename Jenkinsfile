pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                // Compile the .cpp file
                sh 'g++ -o output_file sample.cpp'
            }
            post {
                failure {
                    echo 'Build failed: pipeline failed'
                }
            }
        }
        
        stage('Test') {
            steps {
                // Run the compiled executable
                sh './output_file'
            }
            post {
                failure {
                    echo 'Test failed: pipeline failed'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                // Copy output_file to a remote server using SCP
                sh 'scp output_file user@remote-server:/path/to/deploy'
                
                // Restart the application on the remote server using SSH
                sh 'ssh user@remote-server "sudo systemctl restart myapp"'
            }
            post {
                failure {
                    echo 'Deployment failed: pipeline failed'
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
