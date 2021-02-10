pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn -B -DskipTests clean package'
      }
    }

    stage('Integration test') {
      steps {
        sh 'mvn test'
        junit 'target/surefire-reports/*.xml'
      }
    }

    stage('Sonar') {
      steps {
        sh 'mvn verify sonar:sonar -Dsonar.qualitygate.wait=true -Dsonar.login=f2ef60f5bbe200cddd27bce2422cca9235217d71 -Dsonar.host.url=http://sonar:9000'
      }
    }

  }
}
