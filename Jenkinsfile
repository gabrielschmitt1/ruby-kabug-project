pipeline {
   agent {
       docker {
           image 'qaninja/rubywd'
       }
   }

   stages {
      stage('Build') {
         steps {
            echo 'Building or resolve dependences'
            sh 'rm -rf Gemfile.lock'
            sh 'bundle install'
         }
      }
      stage('Test') {
         steps {
            echo 'Running regression tests'
            sh 'bundle exe cucumber -p ci'
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