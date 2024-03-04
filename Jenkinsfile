pipeline {

    agent any

    environment {
        PATH='C://Program Files//nodejs'
	}

    stages {

       stage('NPM Setup') {
          steps {
           cmd_exec('npm install')
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

def cmd_exec(command) {
    return bat(returnStdout: true, script: "${command}").trim()
}
      
}
}

