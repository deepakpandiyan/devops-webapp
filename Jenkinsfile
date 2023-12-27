pipeline {
  agent {
    node {
      label 'agent1'
    }

  }
  stages {
    stage('clone') {
      steps {
        git(url: 'https://github.com/deepakpandiyan/devops-webapp1', branch: 'master')
      }
    }

    stage('build') {
      parallel {
        stage('build') {
          steps {
            sh '''whoami
date
echo $PATH
pwd
ls -la
./gradlew build --info'''
          }
        }

        stage('P1') {
          steps {
            sh '''date
echo run parallel !!!'''
          }
        }

        stage('P2') {
          steps {
            sh '''date
echo run parallel !!'''
          }
        }

      }
    }

    stage('publish') {
      steps {
        archiveArtifacts(artifacts: 'build/libs/*.war', fingerprint: true, onlyIfSuccessful: true)
      }
    }

  }
}