pipeline {
    agent any

    tools {
        nodejs 'node' // Ensure the Node.js name matches your Jenkins config
    }

    environment {
        CI = 'false'  // Prevent Vite build warnings about CI environments
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/laxminarayan183/Jenkins-tute.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Dev Server') {
            steps {
                sh 'npm run dev'
            }
        }
    }

    post {
        success {
            echo '🎉 React.js Vite app built and served successfully!'
        }
        failure {
            echo '❌ Build failed. Check the logs for details.'
        }
    }
}
