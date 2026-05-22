pipeline {
    agent any

    stages {
        stage('Clonar Repositorio') {
            steps {
                echo 'Clonando repositorio...'
                checkout scm
            }
        }
        stage('Instalar Dependencias') {
            steps {
                echo 'Instalando dependencias...'
            }
        }
        stage('Ejecutar Pruebas') {
            steps {
                echo 'Ejecutando pruebas unitarias...'
            }
        }
        stage('Validar Calidad') {
            steps {
                echo 'Validando calidad del codigo...'
            }
        }
        stage('Resultado') {
            steps {
                echo 'Pipeline completado exitosamente!'
            }
        }
    }

    post {
        success {
            discordSend(
                description: "✅ BUILD EXITOSO - jenkins-ci-demo",
                footer: "Jenkins CI/CD",
                link: env.BUILD_URL,
                result: currentBuild.currentResult,
                title: "Build #${env.BUILD_NUMBER}",
                webhookURL: "https://discord.com/api/webhooks/1507462355435389060/bI4l3JIHOKPODxpBReGlB3XuQtStgdPNB_hsmV_TBhykaGwHdOVco6epl-ZPSWMZ9ytE"
            )
        }
        failure {
            discordSend(
                description: "❌ BUILD FALLIDO - jenkins-ci-demo",
                footer: "Jenkins CI/CD",
                link: env.BUILD_URL,
                result: currentBuild.currentResult,
                title: "Build #${env.BUILD_NUMBER}",
                webhookURL: "TU_WEBHOOK_URL_DE_DISCORD"
            )
        }
    }
}