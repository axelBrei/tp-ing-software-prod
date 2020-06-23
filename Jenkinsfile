pipeline {
  agent any
  stages {
    stage('Build') {
      agent any
      steps {
        sh './gradlew build'
      }
    }

    stage('Test') {
      steps {
        sh './gradlew clean test'
      }
    }

    stage('Analyze') {
      steps {
        sh './gradlew sonarqube -Dsonar.host.url=http://192.168.1.108:9000'
      }
    }

    stage('Jacoco Results') {
      steps {
        sh './gradlew -i test jacocoTestReport'
      }
    }

  }
}