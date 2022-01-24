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
        stage('Deploy Backend') {
            steps {
                deploy adapters: [tomcat8(credentialsId: 'TomcatLogin', path: '', url: 'http://localhost:8001/')], contextPath: 'tasks-backend', war: 'target/tasks-backend.war'
            }
        }
        stage('API Test') {
            steps {
                dir('api-test') {}
                    git credentialsid: 'github_login', url: 'https://github.com/murilosoareslima/tasks-api-test'
                    bat 'mvn test'
                }
            }
        }
    }
}