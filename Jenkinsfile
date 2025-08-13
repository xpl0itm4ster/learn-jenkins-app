pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
               sh '''
               node --version
               npm ci
               ls -la
               '''
            }
        }

        stage('Paralelo') {
            parallel {
                stage('Tarea 1') {
                    steps {
                        echo 'hola 1'
                        echo 'hola 2'
                    }
                }
                stage('Tarea 2') {
                    steps {
                        echo 'hola 3'
                        echo 'hola 4'
                    }
                }
                stage('Tarea 3') {
                    steps {
                        echo 'hola 5'
                    }
                }
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
    }

    post {
        always {
            junit 'test-results/junit.xml'
        }
    }
}
