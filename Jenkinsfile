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
                bat 'npm install'
            }
        }

        stage('Run Dev Server') {
            steps {
                bat 'npm run dev'
            }
        }
        stage('Starting Server') {
            steps {
                echo 'Server started at http://localhost:5173'
            }
        }
    }

    
}
