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
             steps {
                withSonarQubeEnv('sonar-6'){
                sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
                }
             }
  }
    }
}
