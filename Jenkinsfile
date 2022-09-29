pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn -B -DskipTests clean package'
      }
    }

    stage('Test') {
      post {
        always {
          junit 'target/surefire-reports/*.xml'
        }

      }
      
      steps {
        sh 'mvn test'
      }
    }

    stage('Deliver') {
      steps {
        echo 'hello jenkins'
        sh './jenkins/scripts/deliver.sh'
      }
    }

  }
}
