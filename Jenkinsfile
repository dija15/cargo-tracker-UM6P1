pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/dija15/cargo-tracker-UM6P1.git'
            }
        }
         //test and build stage
        stage('Build & Test') {
            steps {
                echo "Java version:"
                bat 'java -version'
                echo "Maven build:"
                bat 'mvn clean verify'
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
