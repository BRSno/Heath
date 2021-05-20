pipeline {
  agent any
  stages {
    stage('Build') {
      parallel {
        stage('Build') {
          steps {
            echo 'Build'
            snDevOpsStep(enabled: true)
          }
        }

        stage('Git') {
          steps {
            git(poll: true, url: 'https://github.com/BRSno/Heath', branch: 'main', changelog: true)
            snDevOpsArtifact(enabled: true, ignoreErrors: true, artifactsPayload: '{"artifacts": [{"name": "heath.war", "version": "1.165","semanticVersion": "1.165.0","repositoryName": "demorepo"}],"branchName":"main"}')
          }
        }

      }
    }

    stage('Test') {
      steps {
        echo 'Test'
        snDevOpsStep(enabled: true)
      }
    }

    stage('Deploy') {
      steps {
        echo 'Deploy'
        snDevOpsStep(enabled: true)
        snDevOpsChange(enabled: true, ignoreErrors: true)
      }
    }

  }
}