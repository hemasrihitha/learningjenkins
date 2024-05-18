pipeline {
  agent any

  triggers {
    cron('H/5 * * * *') // Runs every 5 minutes
  }

  stages {
    stage('Clean Workspace') {
      steps {
        // Clean the workspace
        deleteDir()
      }
    }
    stage('Clone') {
      steps {
        // Clone from your GitHub repository, using the correct branch name and credentials
        git branch: "${env.BRANCH_NAME}",
           credentialsId: 'hemasrihithadendukuri', // Replace with your credential ID
           url: 'https://github.com/hemasrihitha/learningjenkins.git'
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
        // Use a secure HTTPS transfer method (e.g., curl with -u for credentials)
        // **Important:** Replace with your actual deployment command and URL
        sh """
          
          scp -rp ${env.WORKSPACE}/index.html cloud_user@f120574411474f3dbf996693ff893a102c.mylabserver.com:/var/www/html/index.html
        """
      }
    }
  }
}
