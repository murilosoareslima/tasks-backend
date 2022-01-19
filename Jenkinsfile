pipeline {
    agent any
    stages {
        stage ('Build Backend') {
            steps {
                bat 'mvn clean package -DskipTests'
            }
        }
         stage ('Unit Tests') {
            steps {
                bat 'mvn test'
            }
        }
    }
}