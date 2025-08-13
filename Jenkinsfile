pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
            cleanWs()
               sh'''
               node --version
               npm ci
               npm run build
               ls -la
               '''
            }

        }
         stage('Test'){
        steps{
            sh '''
            test -f build/index.html
            npm test
            '''
        }
    }
    }
}
