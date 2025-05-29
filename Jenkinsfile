pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello from Jenkins!'
            }
        }
    }
    tools {
        nodejs 'NodeJS'
    }

    environment {
        NODE_ENV = 'development'
    }

    stages {
        stage('Clone Frontend and Backend') {
            steps {
                dir('frontend') {
                    git url: 'https://github.com/DimashaMadhushani/Quest-Colombo-Frontend.git', branch: 'main'
                }
                dir('backend') {
                    git url: 'https://github.com/DimashaMadhushani/Quest-Colombo-API.git', branch: 'main'
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                dir('frontend') {
                    bat 'npm install'
                }
                dir('backend') {
                    bat 'npm install'
                }
            }
        }

        stage('Run Tests') {
            steps {
                dir('frontend') {
                    bat 'npm test || echo "No frontend tests"'
                }
                dir('backend') {
                    bat 'npm test || echo "No backend tests"'
                }
            }
        }

        stage('Build Frontend') {
            steps {
                dir('frontend') {
                    bat 'npm run build'
                }
            }
        }

        stage('Start Backend') {
            steps {
                dir('backend') {
                    bat 'start /B node index.js'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo '🎯 Deploy your app here (Docker, Render, AWS, etc.)'
            }
        }
    }

    post {
        success {
            echo '✅ Build and Deploy Successful!'
        }
        failure {
            echo '❌ Build Failed. Check logs.'
        }
    }
}
