pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/Ushareddy1310/Netflix'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build('netflix-clone-image')
                }
            }
        }

        stage('Deploy Docker Container') {
            steps {
                script {
                    sh 'docker rm -f netflix-clone || true'
                    sh 'docker run -d -p 80:80 --name netflix-clone netflix-clone-image'
                }
            }
        }
    }
}
