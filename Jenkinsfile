pipeline {
    agent none
    stages {
        stage('Build Frontend') {
            agent { docker { image 'my-node-agent' } }
            when {
                changeset "**/frontend/*.*"
                beforeAgent true
            }
            steps {
                dir('frontend') {
                  sh 'npm install'
                  sh '...'
                }
            }
        }
        stage('Build Web') {
            agent { docker { image 'my-maven-agent' } }
            when {
                changeset "**/backend/web/*.*"
                beforeAgent true
            }
            steps {
               dir ('backend/web') {
                sh 'mvn -B -DskipTests clean package'
                sh '...'
               }
            }
        }
        stage('Build REST API') {
            agent { docker { image 'my-golang-agent' } }
            when {
                changeset "**/backend/api/*.*"
                beforeAgent true
            }
            steps {
               dir ('backend/api') {
                 sh 'go build'
                 sh '...'
               }
            }
        }
    }
}
