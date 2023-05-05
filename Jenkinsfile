pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        bat 'test'
      }
    }

    stage('Test') {
      parallel {
        stage('unitaire') {
          steps {
            bat 'php bin/phpunit tests/unit'
          }
        }

        stage('integration') {
          steps {
            bat 'php bin/phpunit tests/integration'
          }
        }

        stage('fonctionnel') {
          steps {
            bat 'php bin/phpunit tests/fonctionnel'
          }
        }

      }
    }

    stage('deploy') {
      steps {
        bat 'symfony server:start'
      }
    }

  }
}