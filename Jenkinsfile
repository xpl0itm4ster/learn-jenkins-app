pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
               sh'''
               ls -la
               node --version
               npm ci
               npm run build
               '''
            }
        }
    }
}
