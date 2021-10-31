pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        git(url: 'https://github.com/Nachiten/ing-en-sw-tp-testing', branch: 'master')
        withGradle() {
          sh '''echo Building Proyect
./gradlew build'''
        }

      }
    }

    stage('Test') {
      steps {
        sh '''echo Testing Proyect
./gradlew test'''
      }
    }

    stage('Validate') {
      steps {
        sh '''echo Validating Proyect
./gradlew check'''
      }
    }

    stage('Analyse') {
      withSonarQubeEnv() {
        sh "./gradlew sonarqube"
      }
    }

    stage('Deploy') {
      steps {
        sh '''echo Deploying Proyect
./gradlew bootRun'''
      }
    }

  }
}