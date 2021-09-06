pipeline {
  agent any
  stages {
    stage('Checkout SCM') {
      steps {
        git(url: 'https://github.com/sathishmanthani/reader.git', branch: 'master', poll: true)
      }
    }

    stage('prep env') {
      steps {
        sh '''python -m pip install flake8 pytest pytest-cov twine
pip freeze > requirements.txt
'''
      }
    }

  }
}