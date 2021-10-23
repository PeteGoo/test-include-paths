pipeline {

  agent any

  stages {
    stage('build') {
      steps{
        script {
          echo "Hello World:"
          commitHistory.includedCommits.each { item ->
            sh "echo Commit: ${item.owner}/${item.repo}:${item.branch} ${item.commitId} ${item.authorName}\\<${item.authorEmail}\\> ${item.timestamp} ${item.comment}"
            sh "this is not a program - forced failure"
          }
        }
      }
    }
  }
}
