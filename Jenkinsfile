pipeline {
  agent any
  stages {
    stage('Primer Estado') {
      steps {
        sh 'cat /etc/passwd'
        sh 'echo "ejecutado correctamente"'
      }
    }

    stage('copia ficheros') {
      parallel {
        stage('copia ficheros') {
          steps {
            sh 'echo "copiando ficheros"'
          }
        }

        stage('') {
          steps {
            sh 'sleep 15'
          }
        }

      }
    }

    stage('notificaciones') {
      parallel {
        stage('notificaciones') {
          steps {
            emailext(subject: 'testClase Pipeline', body: 'Esto es un test del correo', attachLog: true, to: 'cesarsueca@gmail.com')
          }
        }

        stage('') {
          steps {
            sh 'curl -X POST -H "Content-Type: application/json" -d "{\\"chat_id\\": \\"902285901\\", \\"text\\": \\"Falló la tarea $JOB_NAME!! $BUILD_NUMBER,  \\", \\"disable_notification\\": false}" https://api.telegram.org/bot6972167273:AAFfUCU_9JQyRVkQSbftk_Sc3FVqSpE_SEg/sendMessage'
            sh 'echo "Enviado mensaje telegram"'
          }
        }

      }
    }

  }
}
