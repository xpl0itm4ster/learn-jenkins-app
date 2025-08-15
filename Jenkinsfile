pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
               sh '''
               node --version
               npm ci
               npm run build
               '''
            }
        }



        stage('Test') {
            steps {
                sh '''
                test -f build/index.html
                npm test
                '''
            }
        }

        stage('Deploy') {
                    steps {
                    sh '''
                    npm i netlify-cli
                    node_modules/.bin/netlify --version

                    '''
                    }
                }

    }

    post {
        always {
            junit 'test-results/junit.xml'
        }
    }
}
