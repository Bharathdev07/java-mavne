pipeline {
    agent any

    tools {
        maven 'maven' // Ensure 'maven' is configured in Jenkins Global Tool Configuration
    }

    environment {
        GIT_BRANCH_NAME = env.BRANCH_NAME ?: sh(returnStdout: true, script: "git rev-parse --abbrev-ref HEAD").trim()
    }

    stages {
        stage('Filter Branch') {
            when {
                expression { env.BRANCH_NAME && env.BRANCH_NAME.startsWith('feature/') }
            }
            steps {
                echo "Triggering pipeline for branch: ${env.BRANCH_NAME}"
            }
        }

        stage('Checkout Code') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/feature/*']],
                    userRemoteConfigs: [[url: 'https://github.com/Bharathdev07/java-mavne.git']]
                ])
            }
        }

        stage('Build') {
            steps {
                echo 'Build stage executed'
            }
        }
    }

    post {
        always {
            echo "Pipeline completed for branch: ${env.BRANCH_NAME}"
        }
    }
}
