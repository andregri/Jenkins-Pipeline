pipeline {
    agent { docker { image 'maven:3.8.4-openjdk-11-slim' } }
    environment {
        STAGE = 'debug'
    }
    stages {
        stage('build') {
            steps {
                sh "echo Start building ${STAGE} env"
                sh 'mkdir -p build'
                sh 'touch build/app.xcd'
                sh 'mvn --version'
            }
        }
        stage('test') {
            steps {
                sh 'cat tmp'
            }
        }
        stage('deploy - staging') {
            steps {
                sh 'echo hello > tmp'    
            }
        }
        stage('deploy - production') {
            steps {
                input 'Deploy to production?'
                sh 'echo production > tmp'   
            }
        }
    }
    post {
        always {
            archiveArtifacts artifacts: 'build/*.xcd', fingerprint: true  
        }
        success {
            sh 'rm tmp'
        }
    }
}
