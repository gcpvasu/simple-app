pipeline {
    agent any
    tools {
        maven 'maven3'
    }
    stages{
        stage("Build") {
            steps{
                nexusArtifactUploader artifacts: [
                    [
                        artifactId: 'simple-app',
                        classifier: '', 
                        file: 'target/simple-app-1.0.0.war', 
                        type: 'war'
                    ]
                ], 
                credentialsId: 'nexus3', 
                groupId: 'in.javahome', 
                nexusUrl: '10.128.0.44:8081', 
                nexusVersion: 'nexus2', 
                protocol: 'http',
                repository: 'http://35.224.132.130:8081/repository/simpleapp-release/', 
                version: '1.0.0'
            }
        }
    }
}