pipeline {
  agent {
    node {
      label 'master'
    }

  }
  stages {
    stage('Clone') {
      steps {
        git 'https://github.com/lsmall/devops-webapp'
      }
    }

    stage('Build') {
      parallel {
        stage('Build') {
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
echo running in parallel!'''
          }
        }

        stage('P2') {
          steps {
            sh '''date
echo running in parallel!'''
          }
        }

      }
    }

    stage('Publish') {
      steps {
        archiveArtifacts(artifacts: 'build/libs/*.war', fingerprint: true, onlyIfSuccessful: true)
      }
    }

  }
}