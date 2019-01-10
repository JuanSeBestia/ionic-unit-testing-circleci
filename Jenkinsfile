pipeline {

    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'true' 
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
             sh 'ionic cordova build ios --release'
             
          }
       }

       stage('Android Build') {
          steps {
               sh 'ionic cordova build android --release'
               
          }
       }

       stage('APK Sign') {
          steps {
            // sh 'jarsigner -storepass your_password -keystore keys/yourkey.keystore platforms/android/app/build/outputs/apk/release/app-release-unsigned.apk nameApp'
              echo "Android"
          }
       }



      stage('Stage Web Build') {
          steps {
              sh 'npm run build --prod'
          }
       }

        stage('Publish Firebase Web') {
          steps {
              //sh 'firebase deploy --token "YourTokenKey"'
              echo 'Firebase Deploy'
          }
       }

        stage('Publish iOS') {
          steps {   
              echo "Publish iOS"
          }
       }

        stage('Publish Android') {
          steps {
              echo "Publish Android"
          }
       }

    }
}