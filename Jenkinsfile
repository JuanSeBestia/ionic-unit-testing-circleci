pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('NPM Setup') {
      steps {
        echo "Branch is ${env.BRANCH_NAME}..."
        sh 'npm install'
      }
    }
    stage('IOS Build') {
      steps {
        echo 'IOS BUILD'
      }
    }
    stage('Android Build') {
      steps {
        echo 'Android build'
      }
    }
    stage('APK Sign') {
      steps {
        echo 'Android SING'
      }
    }
    stage('Stage Web Build') {
      steps {
        sh 'npm run build:prod'
      }
    }
    stage('Stage test') {
      steps {
        sh 'npm run build --prod'
        sh 'npm run tslint'
      }
    }
    stage('Publish Firebase Web') {
      steps {
        echo 'Firebase Deploy'
      }
    }
    stage('Publish iOS') {
      steps {
        echo 'Publish iOS'
      }
    }
    stage('Publish Android') {
      steps {
        echo 'Publish Android'
      }
    }
    stage('msg') {
      steps {
        echo 'todo ok'
      }
    }
  }
  environment {
    CI = 'true'
  }
}