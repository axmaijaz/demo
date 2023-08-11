pipeline {
    agent any

    environment {
        // DOCKER_HUB_USERNAME = credentials('docker-hub-username')
        // DOCKER_HUB_PASSWORD = credentials('docker-hub-password')
        DOCKER_HUB_CREDENTIALS = credentials('cred-dockerhub')
        DOCKER_IMAGE_NAME = 'pipeline-dkh-img'
    }


stages {
	    
	      stage('Build Image') {
            steps {
                script {
                //  dockerfile = "Dockerfile"
                 sh "ls"
                 sh "pwd"
                 sh "docker build -f Dockerfile . -t  asmaijaz/${DOCKER_IMAGE_NAME}:${env.BUILD_NUMBER}"
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                   // Log in to Docker Hub using the access token
                    sh "echo Asma1910** | docker login -u asmaijaz --password-stdin "
                    // sh "docker login -u asmaijaz -p ${DOCKER_HUB_CREDENTIALS}"

                    // Push the image to Docker Hub
                    sh "docker push asmaijaz/${DOCKER_IMAGE_NAME}:${env.BUILD_NUMBER}"

                    
                   }
                }
            }
}
}
