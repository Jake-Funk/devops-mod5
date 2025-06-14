pipeline {
    agent any

    tools { go '1.24'}

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'go build hello.go'
                archiveArtifacts artifacts: 'hello', fingerprint: true
            }
        }
        stage('Test') {
            steps {
                sh "./hello"
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
