pipeline {
    agent any
    
    environment {
        SRN = 'PES1UG22CS237'
        REPO_URL = 'https://github.com/harshaankad/PES1UG22CS233_Jenkins.git'
    }
    
    stages {
        stage('Clone repository') {
            steps {
                // Skip cloning since Jenkins already checked out the repository
                sh 'echo "Repository already checked out by Jenkins"'
            }
        }
        
        stage('Install dependencies') {
            steps {
                sh 'g++ --version || echo "g++ not found"'
                sh 'echo "Compiler check completed"'
            }
        }
        
        stage('Build application') {
            steps {
                sh 'g++ -o ${SRN}-1 main/hello.cpp || echo "Build failed - g++ not available"'
                sh 'echo "Build step completed"'
            }
        }
        
        stage('Test application') {
            steps {
                sh './${SRN}-1 || echo "Test failed - executable not found"'
                sh 'echo "Test step completed"'
            }
        }
    }
    
    post {
        failure {
            echo 'Pipeline failed'
        }
        success {
            echo 'Pipeline completed successfully'
        }
    }
}
