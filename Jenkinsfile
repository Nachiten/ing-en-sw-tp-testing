pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git(url: 'https://github.com/Nachiten/ing-en-sw-tp-testing', branch: 'master')
        withGradle() {
          sh 'gradle build'
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
        bat 'gradlew bootRun'
      }
    }

  }
}