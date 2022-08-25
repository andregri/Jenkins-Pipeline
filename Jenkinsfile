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
        always {
            archiveArtifacts artifacts: 'build/*.xcd', fingerprint: true  
        }
        success {
            sh 'rm tmp'
            mail to: 'febavi1961@vpsrec.com',
                 subject: "Successful pipeline ${currentBuild.fullDisplayName}",
                 body: "Pipeline #${env.BUILD_NUMBER} was successful"
        }
    }
}
