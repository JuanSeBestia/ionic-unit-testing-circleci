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
            withNPM(npmrcConfig:'my-custom-npmrc') {
                echo "Performing npm build..."
                sh 'npm install'
            }
         }
       }

       stage('IOS Build') {
          steps {
                
              // sh 'ionic cordova build ios --release'
              echo "IOS BUILD"
             
          }
       }

       stage('Android Build') {
          steps {
              // sh 'ionic cordova build android --release'
              echo "Android build" 
          }
       }

       stage('APK Sign') {
          steps {
              // sh 'jarsigner -storepass your_password -keystore keys/yourkey.keystore platforms/android/app/build/outputs/apk/release/app-release-unsigned.apk nameApp'
              echo "Android SING"
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