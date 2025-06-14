pipeline {
    agent any

    tools {
        go '1.24'
        jfrog 'jfrog-cli'
    }

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
                // Configure Go project's repositories
                jf 'go-config --repo-resolve=devops-class-go --repo-deploy=devops-class-go-local'

                // Build the project with go and resolve the project dependencies from Artifactory
                jf 'go build --build-name=hello --build-number=1 hello.go'

                // Publish version v1.0.0 of the package to the go-local repository in Artifactory
                jf 'go-publish v1.0.0 --build-name=hello --build-number=1'
            }
        }
    }
}
