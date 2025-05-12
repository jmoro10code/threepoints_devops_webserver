pipeline {
    agent any

    options {
        disableConcurrentBuilds()
        buildDiscarder(logRotator(numToKeepStr: '10'))
    }

    environment {
        IMAGE_NAME = "devops_ws"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Pruebas de SAST') {
            steps {
                echo "Ejecución de pruebas de SAST"
            }
        }

        stage('Build') {
            steps {
                script {

                    sh "docker build -t ${env.IMAGE_NAME} ."
                }
            }
        }
    }

    post {
        success {
            echo "Pipeline completado con éxito."
        }
        failure {
            echo "Ha fallado alguna etapa del pipeline."
        }
    }
}