pipeline {
    agent {
       docker {
        image 'maven'
        args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
         stage('SonarQube server') {
             steps {
                withSonarQubeEnv('sonar-6'){
                    sh "mvn sonar:sonar"
                }
             }
  }
    }
}
