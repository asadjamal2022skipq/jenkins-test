pipeline {
    agent any
    stages {
        stage('Test') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
                sh 'cp README.md /home/shahzil/'
            }
        }
    }
    post {
        always {
            echo 'The build has completed.'
        }
        success {
            echo 'Build was sucessful'
        }
        failure {
            echo 'Current build failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}
