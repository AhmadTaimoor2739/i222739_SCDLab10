pipeline {
    agent any

    environment {
        BUILD_TIMESTAMP = new Date().format("yyyy-MM-dd HH:mm:ss")
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/AhmadTaimoor2739/i222739_SCDLab10.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'npm test'
            }
        }

        stage('Build Info') {
            steps {
                script {
                    echo "--------------------------------------"
                    echo "Build #${env.BUILD_NUMBER}"
                    echo "Triggered at: ${env.BUILD_TIMESTAMP}"
                    if (env.GIT_COMMIT) {
                        echo "Triggered by GitHub Webhook ✅"
                    } else {
                        echo "Manually triggered build 🧑‍💻"
                    }
                    echo "--------------------------------------"
                }
            }
        }
    }

    post {
        success {
            echo '✅ Build and tests successful!'
        }
        failure {
            echo '❌ Build failed or tests failed!'
        }
    }
}
