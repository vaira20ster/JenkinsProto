pipeline{
  agent none
  stages{
    stage('checkout'){
      agent any
      steps{
        echo 'checkout the solution...'
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '2497c276-8f54-4c22-b270-c8703a465790', url: 'https://github.com/vaira20ster/JenkinsProto.git']]])
      }
    }
    stage('build'){
      parallel {
        stage('consolebuild'){
           agent{label 'VairamuthuPC'}
      steps{
        checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '2497c276-8f54-4c22-b270-c8703a465790', url: 'https://github.com/vaira20ster/JenkinsProto.git']]])
        echo 'Building the solution...'
        bat "\"${tool 'BuildVS'}\" ${WORKSPACE}/ConsoleApp15/ConsoleApp15.sln /m /p:Configuration=Debug /p:Platform=\"Any CPU\""
        archiveArtifacts artifacts: 'ConsoleApp15/ConsoleApp15/bin/Debug/*.exe'
        
      }
        }
        stage('enginebuild'){
           agent{label 'master'}
      steps{
        echo 'Building the solution...'
        bat "\"${tool 'BuildVS'}\" ${WORKSPACE}/Engine/Engine.sln /m /p:Configuration=Debug /p:Platform=\"Any CPU\""
        archiveArtifacts artifacts: 'Engine/Engine/bin/Debug/*.exe'
      }
        }
      }
    }
  }
  post{
    success {
      mail bcc: '', body: 'Body', cc: '', from: '', replyTo: '', subject: 'Subject', to: 'vairamuthu@solitontech.com'
    }
  }
}
