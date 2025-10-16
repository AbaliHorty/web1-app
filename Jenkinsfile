pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/AbaliHorty/web1-app.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                sh './build.sh' // replace with your build command (e.g. mvn clean install)
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh './test.sh' // replace with your test command
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo 'Deploying to production...'
                sh './deploy.sh' // replace with your deploy command
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            cleanWs()
        }
    }
}
