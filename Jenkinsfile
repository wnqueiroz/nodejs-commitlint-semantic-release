node {
  deleteDir()

  stage('Checkout') {
    checkout scm
  }

  stage('Debug Commit') {
    sh "git config --global user.email \"jenkins@jenkins.com\""
    sh "git config --global user.name \"Jenkins\""

    sh "git commit -m \"fix: foo\" --allow-empty"
    sh "git tag foo"

    withCredentials([[
      $class: 'UsernamePasswordMultiBinding',
      credentialsId: 'eb5e0512-972a-4e10-a6f1-d1570f3e1849',
      usernameVariable: 'GIT_USERNAME',
      passwordVariable: 'GIT_PASSWORD'
    ]]) {
      sh 'git push --follow-tags origin master'
    }
  }
}