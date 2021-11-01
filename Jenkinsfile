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
      steps {
        sh './gradlew sonarqube -Dsonar.projectKey=IngEnSw -Dsonar.host.url=http://sonarqube:9000/ -Dsonar.login=0e991cebaaf94404769566bba7b7bfca04e49559 --stacktrace'
      }
    }

    stage('Jacoco') {
      steps {
        echo 'Generating Jacoco Test Report'
        sh '''./gradlew -i test jacocoTestReport --stacktrace
git add .
git commit -m "testing jenkins"
git push originNachiten master'''
      }
    }

    stage('Deploy') {
      environment {
        SERVER_PORT = '8888'
      }
      steps {
        sh 'echo Deploying Proyect...'
      }
    }

  }
}