@Library("Shared") _
pipeline {
    agent { label 'nerd' }

    stages {
        stage('Hello'){
            steps{
                script{
                    hello()
                }
            }
        }
        stage('Code') {
            steps {
                script{
                    clone("https://github.com/mukthadeer01/django-notes-app.git", "main")
                }
            }
        }

        stage('Build') {
            steps {
                script{
                    docker_build("notes-app", "latest", "mukthadeer01")
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
                script{
                    docker_push("notes-app", "latest", "mukthadeer01")
                }
            }
        }
        stage('Deploy') {
            steps {
                sh "docker compose down && docker compose up -d"
            }
        }   
    }
}
