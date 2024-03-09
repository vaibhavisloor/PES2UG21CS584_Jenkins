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
                // Only print an echo message for deployment
                echo 'Deployment step: Just printing this message'
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
