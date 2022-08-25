pipeline {
    agent { docker { image 'maven:3.8.4-openjdk-11-slim' } }
    stages {
        stage('build') {
            steps {
                sh 'echo Start building...'
                sh 'mvn --version'
            }
        }
        stage('deploy') {
            steps {
                sh 'echo hello > tmp'    
            }
        }
        stage('test') {
            steps {
                sh 'cat tmp'
            }
        }
    }
    post {
        success {
            sh 'rm tmp'
        }
    }
}
