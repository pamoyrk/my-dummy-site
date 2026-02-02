pipeline {
  agent any
  environment {
    GITHUB_REPO = 'pamoyrk/my-dummy-site'
  }
  stages {
    stage('Checkout') {
      steps { checkout scm }
    }
    stage('Deploy to GitHub Pages') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'GITHUB_TOKEN', usernameVariable: 'GIT_USER', passwordVariable: 'GIT_TOKEN')]) {
          bat '''
            git config user.email "wei96word@gmail.com"
            git config user.name "pamoyrk"
            git checkout main
            git checkout -B gh-pages
            git add -A
            git commit -m "Deploy" || echo "No changes to commit"
            git push https://%GIT_USER%:%GIT_TOKEN%@github.com/%GITHUB_REPO%.git gh-pages --force
          '''
        }
      }
    }
  }
}
