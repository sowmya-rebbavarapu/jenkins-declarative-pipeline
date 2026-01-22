pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the application...'
                dir('ci-demo') {
                    // Create build folder only if it doesn't exist
                    bat '''
                    if not exist build mkdir build
                    echo Build successful > build\\build.txt
                    '''
                }
            }
        }

        stage('Test') {
            steps {
                dir('ci-demo') {
                    // Run Maven tests
                    bat 'mvn test'
                }
                // Publish JUnit test results
                junit 'ci-demo/target/surefire-reports/*.xml'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline succeeded'
        }
        failure {
            echo '❌ Pipeline failed - deployment stopped'
        }
    }
}
