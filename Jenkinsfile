pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/YuvaDaraneePrabakar/DockerSwe.git'
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
                        sh 'docker login -u yuvadaranee -p Success@143'
                    }
                }
            }
        }
        stage('Docker Test') {
            steps {
                script {
                    sh 'docker tag worldjavaapp yuvadaranee/worldjavaapp'
                    sh 'docker push yuvadaranee/worldjavaapp:latest'
                }
            }
        }
    }
}
