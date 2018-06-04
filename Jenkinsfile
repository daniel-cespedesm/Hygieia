pipeline {
  agent { label "Hygieia-node" }
  stages {
    stage ('Initialize') {
      steps {
        sh '''
          echo "PATH = ${PATH}"
          echo "M2_HOME = ${M2_HOME}"
        '''
      }
    }
    stage('Build') {
      steps {
        sh 'mvn clean install'
      }
      post {
        failure {
          sh 'mvn clean install -rf :UI'
        }
      }
    }
    stage('Dockerize') {
      steps {
        sh 'docker-compose build'
      }
    }
  }
}
