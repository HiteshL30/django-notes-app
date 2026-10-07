@Library('Shared') _
pipeline {
    agent {label 'vinod'}

    stages {
        stage('clone') {
            steps {
                script{
                    code('https://github.com/HiteshL30/django-notes-app.git', 'main')
                }
            }
        }
        stage('build') {
            steps {
                script{
                    docker_build('notes-app','latest','hlanjewar')
                }
            }
        }
        stage('push') {
            steps {
                script{
                    docker_push('notes-app','latest','hlanjewar')
                }
            }
        }
        
        stage('deploy') {
            steps {
                sh 'docker compose down && docker compose up -d'
            }
        }
    }
}
