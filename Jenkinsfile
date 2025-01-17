pipeline {
    agent any

    tools {
        maven 'maven' // Ensure 'maven' is configured in Jenkins Global Tool Configuration
    }

    stages {
        stage('Set Environment Variables') {
            steps {
                script {
                    env.GIT_BRANCH_NAME = sh(
                        returnStdout: true, 
                        script: "git rev-parse --abbrev-ref HEAD"
                    ).trim()
                }
                echo "Current Git Branch: ${env.GIT_BRANCH_NAME}"
            }
        }

        stage('Filter Branch') {
            when {
                expression { env.GIT_BRANCH_NAME && env.GIT_BRANCH_NAME.startsWith('feature/') }
            }
            steps {
                echo "Triggering pipeline for branch: ${env.GIT_BRANCH_NAME}"
            }
        }

        stage('Checkout Code') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: "${env.GIT_BRANCH_NAME}"]],
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
            echo "Pipeline completed for branch: ${env.GIT_BRANCH_NAME}"
        }
    }
}
