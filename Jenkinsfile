pipeline {
    agent any
    tools {
        nodejs 'NodeJS' // Name of your NodeJS installation in Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub
                git url: 'https://github.com/imrithwik1908/my_node_app',
                    branch: 'master'
            }
        }
        stage('Install Dependencies') {
            steps {
                // Install Node.js dependencies
                sh 'npm install'
            }
        }
        stage('Run Application') {
            steps {
                // Run the application (optional)
                sh 'node app.js &'
            }
        }
    }
    post {
        success {
            echo 'Build was successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
