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
        sh '''python -m venv .
source Scripts/activate
python -m pip install flake8 pytest pytest-cov twine
python -m pip freeze > requirements.txt
'''
      }
    }

    stage('build') {
      steps {
        sh '''pwd
python setup.py install
cd reader
python -m flake8
cd ../tests
python -m pytest -v --cov
'''
      }
    }

    stage('test') {
      steps {
        sh '''
python setup.py sdist bdist_wheel

cd dist
tar tzf realpython-reader-1.0.0.tar.gz
#twine check dist/*
'''
      }
    }

  }
}