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
         stage('SonarQube') {
             environment {
                scannerHome = tool 'SonarQubeScanner'
            }
             steps {
                withSonarQubeEnv('sonar-6'){
                    sh "${scannerHome}/bin/sonar-scanner"
                }
             }
  }
    }
}
