pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Build'
          }
        }

        stage('Git') {
          steps {
            git(poll: true, url: 'https://github.com/BRSno/Heath', branch: 'main')
          }
        }

      }
    }

    stage('Test') {
      steps {
        echo 'Test'
        snDevOpsChange(enabled: true, ignoreErrors: true)
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploy'
      }
    }

  }
}