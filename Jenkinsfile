pipeline{
  agent none
  stages{
    stage('checkout'){
      agent any
      steps{
        echo 'checkout the solution...'
        sleep 5
      }
    }
    stage('build'){
      parallel {
        stage('consolebuild'){
           agent{label 'VairamuthuPC'}
      steps{
        sleep 5
        echo 'Building the solution...'
        sleep 15
      }
        }
        stage('enginebuild'){
           agent{label 'master'}
      steps{
        echo 'Building the solution...'
        sleep 5
      }
        }
      }
    }
  }
}
