pipeline {
    agent any

    stages {
        stage('Clean Workspace') {
            steps {
                // Clean the workspace
                deleteDir()
            }
        }
        stage('Clone') {
            steps {
                // Clone from your GitHub repository, using the correct branch name
                git branch: "${env.BRANCH_NAME}", url: 'git@github.com:hemasrihitha/learningjenkins.git'
            }
        }


        stage('Build') {
            steps {
                // Print build started
                echo 'Build started'
            }
        }

        stage('Test') {
            steps {
                // Print test started
                echo 'Test started'
            }
        }

        stage('Deploy') {
            steps {
                // SCP files
                sh 'scp -rp index.html f120574411474f3dbf996693ff893a101d.mylabserver.com:/var/www/html/'
            }
        }
    }
}
