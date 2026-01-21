pipeline {
    agent any

    triggers {
        githubPush()   
    }

    tools {
        jdk 'jdk17'
        maven 'Maven'
    }

    stages {
        stage('Build & Test') {
            steps {
                bat '''
                    java -version
                    mvn clean verify
                '''
            }
        }
    }

    stages {

        stage('Clone') {
            steps {
                git branch: 'develop', url: 'https://github.com/akito-sama/cargo-tracker.git'
            }
        }

        stage('Build & Test with Coverage') {
            steps {
                bat 'mvn clean verify'
            }
        }

        
    }
//
    post {
        success {
            echo 'Build et analyse terminés avec succès !'
        }
        failure {
            echo 'Échec du build ou des tests.'
        }
    }
}
