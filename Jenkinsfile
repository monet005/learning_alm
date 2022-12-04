pipeline {
    agent { label 'pi-1' }
    stages {
        stage('Docker Build') {
            steps {
                sh 'docker build -t ramon/python_app:latest .'
            }
        stage('Publish to Nexus Repository Manager') {
            steps {
                  nexusArtifactUploader(
                    nexusVersion: 'nexus3',
                    protocol: 'http',
                    nexusUrl: '192.168.0.142:8081',
                    groupId: 'com.example',
                    version: '3.43.0-01',
                    repository: 'alm_dockerhub',
                    credentialsId: 'jenkins-user',
                    artifacts: [
                        [artifactId: alm_dockerhub,
                            classifier: '',
                            file: 'python_app',
                            type: 'docker']
                    ]
                 )
            }
        }
        }
    }
}

