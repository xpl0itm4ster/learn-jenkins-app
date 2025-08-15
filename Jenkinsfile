pipeline {
    agent any

    environment{
        NETLIFY_SITE_ID='6611bf79-5332-4172-9a13-a3ef43250e27'
        NETLIFY_AUTH_TOKEN= credentials('netlify-token')
    }

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
                    echo "Deploying to production site id= $NETLIFY_SITE_ID"
                    node_modules/.bin/netlify status
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
