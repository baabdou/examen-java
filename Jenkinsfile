pipeline {
    agent {
       docker {
        image 'maven:3-alpine'
        args '-v /root/.m2:/root/.m2'
        }
    }
    tools {
        maven 'Maven 3.6'
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
         stage('SonarQube analysis') {
             steps {
                withSonarQubeEnv('sonar-6'){
                    sh "${mvnHome}/bin/mvn sonar:sonar"
                }
             }
  }
    }
}
