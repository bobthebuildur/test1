    pipeline {
    agent any
    tools {
        maven "Maven3"
    }
    
    stages {
        stage('Checkout') {
            steps {
                    echo "stage 1"
            }
        }
        
        stage ("Build") {
            steps {
                echo "stage 2"
            }
            
        }   
    }
}
