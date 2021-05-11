node {
    def app
    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
        app = docker.build("abdulrahman14449/express-app")
    }

    stage('Test image') {
        nodejs(nodeJSInstallationName: 'nodejs') {
            sh 'npm install --only=dev'
            sh 'npm test'
     }
   }

   stage('Push image') {
       docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
           app.push("${env.BUILD_NUMBER}")
           app.push("latest")
       }
       echo "Attempting to push Docker build to Docker Hub"
   }
}