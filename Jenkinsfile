pipeline{
  agent any
  stages{
    stage('checkout'){
      steps{
        echo 'checkout the solution...'
        sleep 5
      }
    }
    stage('build'){
      parallel {
        stage('consolebuild'){
      steps{
        echo 'Building the solution...'
        sleep 5
      }
        }
        stage('enginebuild'){
      steps{
        echo 'Building the solution...'
        sleep 5
      }
        }
      }
    }
  }
}
