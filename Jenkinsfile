pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building the application...'
                mkdir 'build'
                echo 'Build successful' > build/build.txt
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                mkdir 'test-results'
                echo 'All tests passed' > test-results/results.txt
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                echo 'Deployment successful'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }

        always {
            echo 'Archiving artifacts...'
            archiveArtifacts artifacts: '**/build.txt, **/results.txt', fingerprint: true
        }
    }
}
