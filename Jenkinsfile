pipeline {
    agent any

    tools {
        jdk 'jdk11'
        maven 'maven3'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-new',
                    url: 'git@github.com:Nagendrakumarredd/poc-1.git'
            }
        }

        stage('Build') {
            steps {
                dir('poc1-app') {
                    sh 'mvn clean package'
                }
            }
        }
        stage('SonarQube Analysis') {
    steps {
        dir('poc1-app') {
            withSonarQubeEnv('sonarqube-new') {
                sh 'mvn sonar:sonar'
            }
        }
    }
}

    }
}
