pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git(url: 'https://github.com/resLotus/tp-ingenieria-en-software-grupo-3-spring-boot-jpetstore', branch: 'master')
        withGradle() {
          bat 'gradle build'
        }

      }
    }

    stage('Test') {
      steps {
        bat 'gradle test'
      }
    }

    stage('Validate') {
      steps {
        bat 'gradlew check'
      }
    }

    stage('Deploy') {
      steps {
        bat 'gradle run'
      }
    }

  }
}