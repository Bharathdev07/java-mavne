pipeline {
    agent any

    tools {
        maven 'maven' // Ensure 'maven' is configured in Jenkins Global Tool Configuration
    }

    environment {
        GIT_BRANCH_NAME = "${env.BRANCH_NAME ?: 'unknown'}"
    }

    stages {
        stage('Filter Branch') {
            when {
                expression { env.BRANCH_NAME.startsWith('feature/') }
            }
            steps {
                echo "Triggering pipeline for branch: ${env.BRANCH_NAME}"
            }
        }

        stage('Checkout Code') {
            when {
                expression { env.BRANCH_NAME.startsWith('feature/') }
            }
            steps {
                git 'https://github.com/Bharathdev07/java-mavne.git'
            }
        }

        stage('Build') {
            when {
                expression { env.BRANCH_NAME.startsWith('feature/') }
            }
            steps {
                echo 'testing done'
            }
        }
    }

    post {
        always {
            echo "Pipeline completed for branch: ${env.BRANCH_NAME}"
        }
    }
}
