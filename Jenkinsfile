pipeline {
  agent any
  stages {
    stage ('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat9(credentialsId: 'tomcat_credential', path: '', url: 'http://localhost:8081')], contextPath: '/pipeline', onFailure: false, war: 'webapp/target/*.war' 
        }
      }
    }
  }
}

