pipeline {
  agent {
    docker {
      image 'python:latest'
    }

  }
  stages {
    stage('build') {
      steps {
        sh 'pip install -r requirements.txt'
      }
    }

    stage('test') {
      post {
        always {
          junit 'test-reports/*.xml'
        }

      }
      steps {
        sh 'python test.py'
      }
    }

    stage('SendMail') {
      steps {
        emailext(subject: '$DEFAULT_SUBJECT', body: '$DEFAULT_CONTENT', attachLog: true, compressLog: true, postsendScript: '$DEFAULT_POSTSEND_SCRIPT', presendScript: '$DEFAULT_PRESEND_SCRIPT', replyTo: '929457098@qq.com', to: '929457098@qq.com')
      }
    }

  }
}