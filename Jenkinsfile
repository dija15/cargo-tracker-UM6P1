pipeline {
    agent any

    triggers {
        githubPush()
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'develop',
                    url: 'https://github.com/akito-sama/cargo-tracker.git'
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
