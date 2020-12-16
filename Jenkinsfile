pipeline {
    agent any
        tools {
            maven 'MAVEN'
            jdk 'JAVA_HOME'
        }
    stages {
        stage ('Build') {
            steps {
                echo "Building Project"
                bat '''
                mvn clean package install
                '''
            }
        }
        stage('Test') {
            steps {
                bat '''
                 mvn -B verify
                '''
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploy"
                deploy adapters: [tomcat9(credentialsId: '30c2ac53-8dd1-4973-8e04-f96fed5a789f', path: '', url: 'http://localhost:8080')], contextPath: 'DemoApplication', war: '**/*.war'
            }
        }
    }
}
