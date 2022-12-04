pipeline {
    agent { label 'pi-1' }
    stages {
        stage('Docker Build') {
            steps {
                sh 'docker build -t ramon/python_app:v1 .'
            }
        }
        stage('Push docker image to nexus') {
            steps {
                sh 'docker login -u jenkins-user -p Ir0nm1n82! 192.168.0.142:8123'
                sh 'docker tag ramon/python_app:v1 192.168.0.142:8123/ramon/python_app:v1'
                sh 'docker push 192.168.0.142:8123/ramon/python_app:latest'
                sh 'docker rmi -f $(docker images --filter=reference="192.168.0.142:8123/ramon/python_app*")'
                sh 'docker logout 192.168.0.142:8123'
            }
        }
    }
}


