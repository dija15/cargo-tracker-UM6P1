pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/dija15/cargo-tracker-UM6P1.git'
            }
        }

        stage('Build & Test') {
            steps {
                bat '''
                    java -version
                    mvn clean verify
                '''
            }
        }
    }

    post {
        success {
            echo 'Build et tests réussis ✅'
        }
        failure {
            echo 'Échec du build ou des tests ❌'
        }
    }
}
