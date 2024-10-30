pipeline {
    agent any

    environment {
        NODE_VERSION = '14' // Specify the Node.js version you want
    }

    stages {
        stage('Clone Repository') {
            steps {
                echo 'Cloning the repository...'
                // Git checkout will happen automatically due to the SCM configuration in Jenkins
            }
        }
        stage('Install NVM and Node.js') {
            steps {
                echo 'Installing NVM and setting up Node.js...'
                sh '''
                    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
                    export NVM_DIR="$HOME/.nvm"
                    . "$NVM_DIR/nvm.sh"
                    nvm install $NODE_VERSION
                    nvm alias default $NODE_VERSION
                '''
            }
        }
        stage('Install Dependencies') {
            steps {
                echo 'Installing project dependencies...'
                sh '''
                    export NVM_DIR="$HOME/.nvm"
                    . "$NVM_DIR/nvm.sh"
                    npm install
                '''
            }
        }
        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                sh '''
                    export NVM_DIR="$HOME/.nvm"
                    . "$NVM_DIR/nvm.sh"
                    npm test
                '''
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Add your deployment commands here, for example:
                // sh 'npm run deploy'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check the logs for details.'
        }
    }
}
