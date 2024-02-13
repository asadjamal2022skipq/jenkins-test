pipeline {
    agent any
    environment {
        DISABLE_AUTH = 'true'
        DB_ENGINE    = 'sqlite'
        GITHUB_TOKEN="your_access_token_here"
    }
    stages {
        stage('Build') {
            steps {
                sh 'echo "Salam World"'
                sh '''
                    echo "Multiline shell steps works too"
                    ls -lah
                '''
                sh 'printenv'
            }
        }
        stage('Test'){
            steps {
                sh 'cp README.md /home/shahzil/'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
            }
        }
    }
    post {
        always {
            echo 'The build has completed.'
            // archiveArtifacts artifacts: 'build/libs/**/*.jar', fingerprint: true
            junit 'build/reports/**/*.xml'
        }
        success {
            echo 'Build was sucessful'
        }
        failure {
            echo 'Current build failed'
            mail to: 'asad.jamal.skipq@gmail.com',
             subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
             body: "Something is wrong with ${env.BUILD_URL}"
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
