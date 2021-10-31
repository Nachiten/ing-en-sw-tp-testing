pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git(url: 'https://github.com/Nachiten/ing-en-sw-tp-testing', branch: 'master')
        withGradle() {
          sh './gradlew build'
        }

      }
    }

    stage('Test') {
      steps {
        sh './gradlew test'
      }
    }

    stage('Validate') {
      steps {
        sh './gradlew check'
      }
    }

    stage('Deploy') {
      steps {
        sh './gradlew bootRun'
      }
    }

  }
}