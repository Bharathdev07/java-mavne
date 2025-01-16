pipeline {
    agent any

    stages {
        stage('github') {
            steps {
                git 'https://github.com/Bharathdev07/java-mavne.git'
            }
        }
stage('build') {
            steps {
                sh 'mvn clean install"
            }
        }
    }
}
