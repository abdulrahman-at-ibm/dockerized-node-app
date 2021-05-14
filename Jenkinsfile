pipeline {
    options {
        timeout(time: 1, unit: 'HOURS')
    }
    agent {
        label 'redhat-0803 && amd64 && docker'
    }
    stages {
        stage('build and push') {
            when {
                branch 'master'
            }
            sh "docker build -t docker/getting-started ."

            steps {
                withDockerRegistry(['https://registry.hub.docker.com', 'docker-hub']) {
                    sh("docker push docker/getting-started")
                }
            }
        }
    }
}
