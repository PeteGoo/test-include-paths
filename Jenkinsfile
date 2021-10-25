pipeline {

  agent any

  stages {
    stage('build') {
      steps{
        script {
          echo "Hello World:"
          commitHistory.includedCommits.each { item ->
            sh "echo Commit: ${item.owner}/${item.repo}:${item.branch} ${item.commitId} ${item.authorName}\\<${item.authorEmail}\\> ${item.timestamp} ${item.comment}"
            sh "Forced Error"
          }
          whateverFunction()
        }
      }
    }
  }
}

import groovy.json.JsonOutput

void whateverFunction() {
    String buildUrl = env.RUN_DISPLAY_URL ?: env.BUILD_LINK ?: ""
    def commits = []
    if(getBinding().hasVariable('commitHistory')) {
        commits = commitHistory.includedCommits.collectEntries{
            ["Id": it.commitId, "Comment": it.comment]
        }
    }
    payload = [
            "BuildEnvironment": "Jenkins",
            "Branch": env.BRANCH_NAME,
            "BuildNumber": "${env.JOB_NAME.replace(' ', '_')}/${env.BUILD_NUMBER}",
            "BuildUrl": buildUrl,
            "VcsType": env.GIT_URL ? "Git" : "<unknown>",
            "VcsRoot": env.GIT_URL,
            "VcsCommitNumber": env.GIT_COMMIT,
            "Commits": commits
    ]
  echo JsonOutput.toJson(payload)
}
