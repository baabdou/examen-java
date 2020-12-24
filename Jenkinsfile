pipeline {
    agent {
    docker {
        image 'maven:3-alpine'
        label 'my-defined-label'
        args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
    }
}
