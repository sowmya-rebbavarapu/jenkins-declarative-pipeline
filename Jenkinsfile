pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building the application...'
                bat '''
                mkdir build
                echo Build successful > build\\build.txt
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat '''
                mkdir test-results
                echo All tests passed > test-results\\results.txt
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                bat 'echo Deployment successful'
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
            archiveArtifacts artifacts: 'build/**, test-results/**', fingerprint: true
        }
    }
}
