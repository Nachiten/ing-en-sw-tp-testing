pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git(url: 'https://github.com/resLotus/tp-ingenieria-en-software-grupo-3-spring-boot-jpetstore', branch: 'master')
        withGradle() {
          sh 'sh \'./gradlew build\''
        }

      }
    }

    stage('Test') {
      steps {
        sh 'gradle test'
      }
    }

    stage('Validate') {
      steps {
        validateDeclarativePipeline 'confirmation.txt'
      }
    }

    stage('Deploy') {
      steps {
        sh 'gradle run'
      }
    }

  }
}