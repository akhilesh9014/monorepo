pipeline {
    agent none
    stages {
        stage('Build Frontend') {
            agent { docker { image 'maven:3.8.4-openjdk-11-slim' } }
            when {
                changeset "backend/*.*"
                beforeAgent true
            }
            steps {
                sh 'mvn --version'
            }
        }
        stage('Build Web') {
            agent { docker { image 'node:16.13.1-alpine' } }
            when {
                changeset "web/*.*"
                beforeAgent true
            }
            steps {
                sh 'node --version'
            }
        }
    }
}
