pipeline {
  agent any

  triggers {
    cron('H/5 * * * *') // Runs every 5 minutes
  }

  stages {
    stage('Check Branch Pattern') {
      when {
        // Skip this stage if the branch name doesn't start with "release/"
        branch !startsWith('dev/')
      }
      steps {
        echo "Branch name '${env.BRANCH_NAME}' does not start with 'release/'. Skipping build and deploy."
      }
    }

    stage('Clean Workspace') {
      when {
        // Only run this stage if the previous stage didn't skip (branch matched the pattern)
        expression { return !stage('Check Branch Pattern').skipped }
      }
      steps {
        // Clean the workspace
        deleteDir()
      }
    }
    stage('Clone') {
      when {
        expression { return !stage('Check Branch Pattern').skipped }
      }
      steps {
        // Clone from your GitHub repository, using the correct branch name and credentials
        git branch: "${env.BRANCH_NAME}",
          credentialsId: 'hemasrihithadendukuri', // Replace with your credential ID
          url: 'https://github.com/hemasrihitha/learningjenkins.git'
      }
    }

    stage('Build') {
      when {
        expression { return !stage('Check Branch Pattern').skipped }
      }
      steps {
        // Print build started
        echo 'Build started'
      }
    }

    stage('Test') {
      when {
        expression { return !stage('Check Branch Pattern').skipped }
      }
      steps {
        // Print test started
        echo 'Test started'
      }
    }

    stage('Deploy') {
      when {
        expression { return !stage('Check Branch Pattern').skipped }
      }
      steps {
        // Use a secure HTTPS transfer method (e.g., curl with -u for credentials)
        // **Important:** Replace with your actual deployment command and URL
        sh """
          echo 'srihitha'
          scp -rp index.html f120574411474f3dbf996693ff893a102c.mylabserver.com:/var/www/html/
        """
      }
    }
  }
}
