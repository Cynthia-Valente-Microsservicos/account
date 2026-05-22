pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Como o pom.xml está na raiz desse repositório, roda direto:
                sh 'mvn -B -DskipTests clean install'
            }
        }
    }
}