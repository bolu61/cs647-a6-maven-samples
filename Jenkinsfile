pipeline {
  agent any
  tools { 
      maven 'Default'
      jdk 'temurin8' 
  }
  stages {
    stage("verify") {
      steps {
        script {
          try {
            sh 'mvn clean test'
          } catch (e) {
            sh 'git bisect start HEAD HEAD~5'
            sh 'git bisect run mvn clean test'
            throw e
          }
        }
      }
    }
  }
}
