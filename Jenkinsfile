pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Add build commands here, if any (e.g., npm build for Node.js applications)
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add commands to execute tests, if any
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying...'
                script {
                    if (env.BRANCH_NAME == 'dev') {
                        // Commands to deploy to development server
                        sh 'scp -r * cloud_user@f120574411474f3dbf996693ff893a101c.mylabserver.com:/var/www/html/'
                    } else if (env.BRANCH_NAME == 'test') {
                        // Commands to deploy to testing server
                        sh 'scp -r * cloud_user@f120574411474f3dbf996693ff893a102c.mylabserver.com:/var/www/html/'
                    } else if (env.BRANCH_NAME == 'pro') {
                        // Commands to deploy to production server
                        sh 'scp -r * cloud_user@f120574411474f3dbf996693ff893a103c.mylabserver.com:/var/www/html/'
                    }
                }
            }
        }
    }
    post {
        always {
            echo 'Cleaning up...'
            // Add any cleanup commands
        }
    }
}
