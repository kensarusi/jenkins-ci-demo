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
        error('ERROR INTENCIONAL: Fallo en pruebas unitarias')
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
                webhookURL: "TU_WEBHOOK_DISCORD"
            )
            emailext(
                subject: "✅ Jenkins Build EXITOSO - #${env.BUILD_NUMBER}",
                body: "<h2>Build Exitoso</h2><p>Proyecto: jenkins-ci-demo</p><p>Build: #${env.BUILD_NUMBER}</p>",
                to: "kensarusi@gmail.com",
                mimeType: 'text/html'
            )
        }
        failure {
            discordSend(
                description: "❌ BUILD FALLIDO - jenkins-ci-demo",
                footer: "Jenkins CI/CD",
                link: env.BUILD_URL,
                result: currentBuild.currentResult,
                title: "Build #${env.BUILD_NUMBER}",
                webhookURL: "TU_WEBHOOK_DISCORD"
            )
            emailext(
                subject: "❌ Jenkins Build FALLIDO - #${env.BUILD_NUMBER}",
                body: "<h2>Build Fallido</h2><p>Proyecto: jenkins-ci-demo</p><p>Build: #${env.BUILD_NUMBER}</p>",
                to: "kensarusi@gmail.com",
                mimeType: 'text/html'
            )
        }
    }
}