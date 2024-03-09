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
                // Add deployment steps if necessary
            }
        }
    }
    
    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}
