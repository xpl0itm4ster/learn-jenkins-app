pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
               sh'''
               node --version
               npm ci
               #npm run build
               ls -la
               '''
            }

        }

        stage{
            parallel{
                 steps {
                echo 'hola 1'
                                echo 'hola 2'

                echo 'hola 13'

                echo 'hola 4'

                echo 'hola 5'

            }
              

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
    post{
        always{
             junit 'test-results/junit.xml'
        }
    }
}
