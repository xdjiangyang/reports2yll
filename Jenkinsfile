pipeline {
  agent any
  stages {
    stage('test') {
      parallel {
        stage('test') {
          steps {
            sh 'ifconfig'
          }
        }
        stage('test1') {
          steps {
            sh 'echo \'This is a test\''
          }
        }
      }
    }
    stage('build') {
      parallel {
        stage('build') {
          steps {
            build 'aaa'
          }
        }
        stage('') {
          steps {
            build 'bbb'
          }
        }
      }
    }
    stage('deploy') {
      steps {
        ws(dir: '/tmp')
      }
    }
  }
}