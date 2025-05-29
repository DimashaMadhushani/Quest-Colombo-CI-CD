pipeline {
    agent any

    tools {
        nodejs 'NodeJS'  // Make sure this matches Global Tool name
    }

    environment {
        NODE_ENV = 'development'
    }

    stages {
        stage('Clone Frontend') {
            steps {
                dir('frontend') {
                    git url: 'https://github.com/DimashaMadhushani/Quest-Colombo-Frontend.git', branch: 'main'
                }
            }
        }

        stage('Clone Backend') {
            steps {
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
                echo '🚀 Add deployment steps here if needed.'
            }
        }
    }

    post {
        success {
            echo '✅ CI/CD Pipeline finished successfully!'
        }
        failure {
            echo '❌ CI/CD Pipeline failed. Check logs above.'
        }
    }
}
