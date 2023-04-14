pipeline {
    any agent

    stages {

        stage ('Build Docker Image') {
            steps {
                script {
                    dockerapp = docker.build("rafaelvcruz/kube-news:${env.BUILD_ID}",'--file ./src/Dockerfile ./src')
                }
            }
        }
        
        stage ('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com','dockerhub'){
                        dockerapp.push('latest')
                        dockerapp.push("${env.BUILD_ID}")
                    }
                }
            }
        }
    }
}