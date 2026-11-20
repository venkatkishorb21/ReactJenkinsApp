
pipeline {
    agent any

    triggers {
        pollSCM('H/2 * * * *')
    }

    tools {
        nodejs 'NodeJS22'
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm ci'
            }
        }

        stage('Run Tests') {
            steps {
                bat 'npm test'
            }
        }

        stage('Build React') {
            steps {
                bat 'npm run build'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'dist/**/*',
                                 fingerprint: true
            }
        }
    }
}
