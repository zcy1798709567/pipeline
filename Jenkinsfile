pipeline {
    agent any

    stages {
        stage('pull code') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'e8c4494c-8956-471c-9828-969a1a0e888a', url: 'http://zhuchengyong@192.168.3.222:10010/r/untitled1.git']]])
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