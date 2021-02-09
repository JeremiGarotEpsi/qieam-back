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
        junit 'target/surefire-reports/*.xml'
      }
    }

    stage('Sonar') {
      steps {
        sh 'mvn verify sonar:sonar -Dsonar.qualitygate.wait=true -Dsonar.login=cf878d3201bc4f1bf2a9c4d9a3a70e7359fff8dd -Dsonar.host.url=http://192.168.1.18:9000'
      }
    }

  }
}