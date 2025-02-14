pipeline {
    agent any

    environment {
        NETLIFY_AUTH_TOKEN = credentials('NETLIFY_AUTH_TOKEN') 
        NETLIFY_SITE_ID = 'b4ab85eb-6648-4056-bbe5-ddb5f2b80445'
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

        stage('Build React App') {
            steps {
                bat 'npm run build'
            }
        }

        stage('Deploy to Netlify') {
            steps {
                bat '''
                npm install netlify-cli -g
                netlify deploy --prod --auth $NETLIFY_AUTH_TOKEN --site $NETLIFY_SITE_ID --dir build
                '''
            }
        }
    }
     post {
        success {
                echo "Deployment Succesfull"
        }
        failure {
                echo 'Deployment Failed'
        }
    }
}
