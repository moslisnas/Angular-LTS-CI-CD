pipeline {
  agent any

  tools {
    nodejs 'NodeJs 18.20.8 - Compatibility with Angular 19.2.15 (LTS)'
  }

  environment {
    CI = 'true'
  }

  stages {
    stage('Checkout') {
      steps {
        git url: 'https://github.com/moslisnas/Angular-LTS-CI-CD.git', branch: 'master'
      }
    }

    stage('Install dependencies') {
      steps {
        sh 'npm ci'
      }
    }

    stage('Lint') {
      steps {
        sh 'npm run lint'
      }
    }

    stage('Build') {
      steps {
        sh 'npm run build -- --configuration=production'
      }
    }

    stage('Tests') {
      steps {
        sh 'npm run test -- --watch=false --browsers=ChromeHeadless'
      }
    }
  }

  post {
    always {
      echo 'Pipeline finished'
    }
    failure {
      echo 'Pipeline failed'
    }
    success {
      echo 'Pipeline succeeded'
    }
  }
}