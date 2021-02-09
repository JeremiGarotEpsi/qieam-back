pipeline {
  agent {
    docker {
      image 'maven:3-alpine'
      args '-v /root/.m2:/root/.m2'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh 'mvn -B -DskipTests clean package'
      }
    }

    stage('Integration test') {
      steps {
        sh 'mvn test'
        junit '*.xml'
      }
    }

  }
}