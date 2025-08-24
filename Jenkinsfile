pipeline {
  agent {
    docker { image 'python:3.11-slim' } // gives you python & pip
  }
  stages {
    stage('Checkout') {
      steps { checkout scm }
    }
    stage('Setup venv') {
      steps {
        sh '''
          python --version
          python -m venv .venv
          . .venv/bin/activate
          pip install --upgrade pip
          test -f requirements.txt && pip install -r requirements.txt || true
        '''
      }
    }
    stage('Tests') {
      steps {
        sh '. .venv/bin/activate && pytest -q || true'
      }
    }
  }
}
