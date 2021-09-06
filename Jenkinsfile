pipeline {
  agent any
  stages {
    stage('Checkout SCM') {
      steps {
        git(url: 'https://github.com/sathishmanthani/reader.git', branch: 'master', poll: true)
      }
    }

  }
}