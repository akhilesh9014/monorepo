pipeline {
    agent none
    stages {
        stage('Build Frontend') {
            when {
                changeset "**/backend/*.*"
                beforeAgent true
            }
            steps {
                dir('backend') {
                  sh 'npm install'
                  sh '...'
                }
            }
        }
        stage('Build Web') {
            when {
                changeset "**/web/*.*"
                beforeAgent true
            }
            steps {
               dir ('web') {
                sh 'mvn -B -DskipTests clean package'
                sh '...'
               }
            }
        }
    }
}
