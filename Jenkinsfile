pipeline {
  agent any
  stages {
    stage('Checkout') { steps { checkout scm } }
    stage('Setup venv') {
      steps {
        sh '''
          python3 -m venv .venv
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
pipeline {
  agent any
  stages {
    stage('Checkout')   { steps { checkout scm } }
    stage('Say hello')  { steps { echo 'Hello from GitHub Pipeline!' } }
  }
}
EOF
