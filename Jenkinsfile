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
                    sh 'mvn sonar:sonar -Dsonar.host.url=http://localhost:9000 Dsonar.login=ca03183c9d89375f149d99fcd2d31b294420bd3a'
                }
             }
  }
    }
}
