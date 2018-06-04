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
        sh 'mvn install clean'
      }
      post {
        success {
          archiveArtifacts artifacts: '*/target/*.jar', fingerprint: true
        }
      }
    }
  }
}
