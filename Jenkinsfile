pipeline {
    agent 
    {
        label 'slave'
    }
    tools {
        gradle "GRADLE_LATEST"
    }
    stages {
        stage('Gradle') {
            steps {
                sh 'gradle --version'
            }
        }
        stage('tasks') {
            steps {
                sh 'gradle tasks'
            }
        }
    }
}
