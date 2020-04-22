pipeline {
   agent any

   stages {
      stage('Build') {
         steps {
            echo 'Building or resolve dependences'
            sh 'bundle install'
         }
      }
      stage('Test') {
         steps {
            echo 'Running regression tests'
         }
      }
      stage('UserAccept') {
         steps {
            echo 'User aceept tests'
            input(message: 'Go to production?', ok: 'Yes')
         }
      }
      stage('Prod') {
         steps {
            echo 'System is ready'
         }
      }
   }
}