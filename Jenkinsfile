pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    docker.build('mydjangoapp:latest')
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    docker.image('mydjangoapp:latest').inside {
                        sh 'python manage.py test'
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    docker.image('mydjangoapp:latest').inside {
                        sh 'python manage.py runserver 0.0.0.0:8000'
                    }
                }
            }
        }
    }
}
