pipeline {
    agent { label 'pi-1' }
    stages {
        stage('Docker Build) {
            steps {
                sh 'docker build ramon/python_app:latest .'
            }
        }
    }
}

