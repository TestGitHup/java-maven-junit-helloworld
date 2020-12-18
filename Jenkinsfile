pipeline {
  agent any
  stages {
    stage('checkout project') {
      steps {
        checkout scm
      }
    }

    stage('build') {
      steps {
        sh 'mvn clean package'
      }
    }

    stage('report') {
      parallel {
        stage('report/archive') {
          steps {
            sh '**/target/surefire-reports/TEST-*.xml'
          }
        }

        stage('junit') {
          steps {
            sh 'target/*.jar'
          }
        }

      }
    }

  }
}