pipeline {
    agent any

    environment {
        IMAGE_NAME = "codecraft-api"
    }

    stages {
        stage('Clonar Repositorio') {
            steps {
                git credentialsId: 'github-credentials', url: 'https://github.com/diegojimenez1029/CodeCraft-API.git', branch: 'main'
            }
        }

        stage('Instalar Dependencias') {
            steps {
                sh 'npm install'
            }
        }

        stage('Ejecutar Pruebas') {
            steps {
                sh 'npm test'
            }
        }

        stage('Construir Imagen Docker') {
            steps {
                script {
                    sh "docker build -t ${IMAGE_NAME} ."
                }
            }
        }
    }
}