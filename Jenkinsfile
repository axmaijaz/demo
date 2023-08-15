pipeline {
    agent any
environment {
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
     stage('Login') {
	 steps {
	      script {
	                   // Log in to Docker Hub using the access token
                    sh "echo Asma1910** | docker login -u asmaijaz --password-stdin "
	       }
	    }
	}

	      
        stage('Push to Docker Hub') {
            steps {
                  script{
                    // Push the image to Docker Hub
                    sh "docker push asmaijaz/${DOCKER_IMAGE_NAME}:${env.BUILD_NUMBER}"
                   }
                }
            }
}
}
