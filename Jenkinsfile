pipeline {
    agent any

    tools {
        maven 'Maven3'    // Make sure 'Maven3' is configured in Jenkins Global Tools
        jdk 'JDK11'       // Also configure JDK11 in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                git branch: 'master', url: 'https://github.com/subhakishore/simple-java-ci-pipeline.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building project...'
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying build...'
                sh '''
                mkdir -p /tmp/deploy
                cp target/*.jar /tmp/deploy/
                '''
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful done!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
