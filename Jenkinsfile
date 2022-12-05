pipeline {
    agent { label 'pi-1' }
    stages {
        stage('Docker Build') {
            steps {
                sh 'docker build -t ramon/python_app:${params.version} .'
            }
        }
        stage('Push docker image to nexus') {
            steps {
                sh 'docker login -u jenkins-user -p Ir0nm1n82! 192.168.0.142:8123'
                sh 'docker tag ramon/python_app:v1 192.168.0.142:8123/ramon/python_app:${params.version}'
                sh 'docker push 192.168.0.142:8123/ramon/python_app:${params.version}'
                sh 'docker rmi -f $(docker images --filter=reference="192.168.0.142:8123/ramon/python_app*" -q)'
                sh 'docker logout 192.168.0.142:8123'
            }
        }
    }
}


