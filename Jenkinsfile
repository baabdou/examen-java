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
         stage('SonarQube analysis') {
           def mvnHome = tool name: 'maven-3', type: 'maven'
             withSonarQubeEnv('sonar-6'){
                 sh "${mvnHome}/bin/mvn sonar:sonar"
    }
  }
    }
}
