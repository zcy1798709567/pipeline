pipeline {
    agent any

    stages {
        stage('pull code') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'ffc30ebc-eefc-4640-b67e-5f85ddc07bd8', url: 'git@github.com:zcy1798709567/pipeline.git']]])
            }
        }
        stage('built code') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('deployment code') {
            steps {
                deploy adapters: [tomcat8(credentialsId: '96c23f60-7313-46aa-bc3e-d2ae7a090618', path: '', url: 'http://192.168.196.130:8080')], contextPath: null, war: 'target/*.war'
            }
        }
    }
}