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
      environment {
        SONARQUBE_PROYECT = 'credentials(\'sonarqube-project\')'
        SONARQUBE_URL = 'credentials(\'sonarqube-url\')'
        SONARQUBE_TOKEN = 'credentials(\'sonarqube-token\')'
      }
      steps {
        sh '''echo Analysing Proyect
./gradlew sonarqube -Dsonar.projectKey=$SONARQUBE_PROYECT -Dsonar.host.url=$SONARQUBE_URL -Dsonar.login=$SONARQUBE_TOKEN --stacktrace'''
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