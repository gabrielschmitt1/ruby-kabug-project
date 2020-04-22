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
            cucumber failedFeaturesNumber: -1, failedScenariosNumber: -1, failedStepsNumber: -1, fileIncludePattern: '**/*.json', jsonReportDirectory: 'logs', pendingStepsNumber: -1, skippedStepsNumber: -1, sortingMethod: 'ALPHABETICAL', undefinedStepsNumber: -1
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