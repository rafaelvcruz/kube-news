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
    }
}