pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git(url: 'https://github.com/resLotus/tp-ingenieria-en-software-grupo-3-spring-boot-jpetstore/tree/master/gradle/wrapper', branch: 'master')
        sh 'gradle build'
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