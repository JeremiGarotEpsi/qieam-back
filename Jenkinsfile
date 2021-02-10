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
        sh 'mvn verify sonar:sonar -Dsonar.qualitygate.wait=true -Dsonar.login=374c719dc3e9483f1652c8fed4f6028e7b5d113b -Dsonar.host.url=http://sonar:9000'
      }
    }

  }
}
