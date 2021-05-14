pipeline {
    options {
        timeout(time: 1, unit: 'HOURS')
    }
    
    agent {
        label 'redhat-0803 && amd64 && docker'
    }
    
    stages {
        stage('build') {
            steps {
                sh "docker build -t abdulrahman14449/dockerized-node-app ."
            }
        }
        stage('push') {
            steps {
                withDockerRegistry([url: "", credentialsId: "docker_hub_id"]) {
                    sh("docker push abdulrahman14449/dockerized-node-app")
                }
            }
        }
    }
}
