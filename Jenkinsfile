pipeline {
    agent any
    tools {
        maven 'maven3'
    }
    stages{
        stage("Build") {
            steps{
                sh script: 'mvn clean package'
            }
        }
        stage("Upload war to Nexus") {
            steps{
                script {
                    def mavenPom = readMavenPom file: 'pom.xml'
                    nexusArtifactUploader artifacts: [
                    [
                        artifactId: 'simple-app',
                        classifier: '', 
                        file: "target/simple-app-${mavenPom.version}.war", 
                        type: 'war'
                    ]
                ], 
                credentialsId: 'nexus3', 
                groupId: 'in.javahome', 
                nexusUrl: '10.128.0.44:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http',
                repository: 'simpleapp-release', 
                version: "${mavenPom.version}"
                }
            }
        }
    }
}