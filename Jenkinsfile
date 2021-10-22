pipeline {

  agent any

  stages {
    stage('build') {
      steps{
        script {
          echo "Hello World:"
          commitHistory.IncludedCommits.each { item ->
            sh "echo Commit: ${item.Owner}/${item.Repo}:${item.Branch} ${item.CommitId} ${item.AuthorName}<${item.AuthorEmail}> ${item.Timestamp} ${item.Comment}"
          }
        }
      }
    }
  }
}
