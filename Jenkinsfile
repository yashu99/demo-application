pipeline {
    agent any
        tools {
            maven 'MAVEN_HOME'
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
                deploy adapters: [tomcat9(credentialsId: '061c9f12-3afe-43ff-9c5f-61d210c0001e', path: '', url: 'http://localhost:9091')], contextPath: 'DemoApplication', war: '**/*.war'
                
            }
        }
    }
}
