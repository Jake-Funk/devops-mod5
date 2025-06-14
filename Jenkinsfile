pipeline {
    agent any

    tools { go '1.24'}

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'go version'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
