    pipeline {
    agent 
    {
        label 'slave'
    }
     environment {
        NEXUS_USER = "nexus3"
        NEXUS_VERSION = "nexus3"
        NEXUS_PROTOCOL = "http"
        NEXUS_URL = "172.31.40.209:8081"
        NEXUS_REPOSITORY = "test-release"
        NEXUS_CREDENTIAL_ID = "nexuslogin"
        ARTVERSION = "${env.BUILD_ID}"
    }

    tools {
        //configure gradle in jenkins and name it as Gradle_latest
        gradle "GRADLE_LATEST" 
    }
    stages {
        stage('Build') {
            steps {
                echo '<--------------- Building --------------->'
                sh 'gradle clean build'
                echo '<------------- Build completed --------------->'
            }
        }


        stage('nexus upload') {
            steps {
                echo '<--------------- Building --------------->'
                nexusArtifactUploader(
                    nexusVersion: "${NEXUS_VERSION}",
                    protocol: "${NEXUS_PROTOCOL}",
                    nexusUrl: "${NEXUS_URL}",
                    groupId: 'com.example',
                    version: version,
                    repository: "${NEXUS_REPOSITORY}",
                    credentialsId: "${NEXUS_CREDENTIAL_ID}",
                    artifacts: [
                      [artifactId: projectName,
                      classifier: '',
                      file: 'my-service-' + version + '.jar',
                      type: 'jar/war']
                echo '<------------- Build completed --------------->'
                    ]
                )    
            }
        }

    }
}
