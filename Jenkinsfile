pipeline {
    agent any
    tools {
        maven 'Maven 3'
        jdk 'Java 8'
    }
    options {
        buildDiscarder(logRotator(artifactNumToKeepStr: '5'))
    }
    stages {
        stage ('Build') {
            steps {
                sh 'sh paper j'
            }
            post {
                success {
                    archiveArtifacts artifacts: 'paperclip.jar', fingerprint: true
                }
            }
        }

        stage ('Deploy') {
            when {
                branch "master"
            }
            steps {
                sh 'echo Skipping'
            }
        }
    }

    post {
        always {
            deleteDir()
        }
    }
}
