pipeline {
  agent {
    label 'nodejs'
  }
  stages {
    stage('Install dependencies') {
      steps {
        sh 'npm ci'
      }
    }

    stage('Check Style') {
      steps {
        sh 'npm run lint'
      }
    }

    stage('Test') {
      steps {
        sh 'npm test'
      }
    }

    stage('Release') {
      steps {
        sh '''
            oc project muwtnp-greetings
            oc apply -f build.yml
            oc start-build greeting-console  --follow --wait
        '''
      }
    }

  }
}
