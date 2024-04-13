pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/YuvaDaraneePrabakar/DockerSwe'
            }
        }
        stage('Docker Build') {
            steps {
                script {
                    sh 'docker build -t worldjavaapp .'
                }
            }
        }
        stage('Docker Login') {
            steps {
                script {
                    withCredentials([string(credentialsId: 'docker', variable: 'dockerhub')]) {
                        sh 'docker login -u swesiva -p Success@143'
                    }
                }
            }
        }
        stage('Docker Test') {
            steps {
                script {
                    sh 'docker tag worldjavaapp swesiva/worldjavaapp'
                    sh 'docker push swesiva/worldjavaapp:latest'
                }
            }
        }
    }
}
