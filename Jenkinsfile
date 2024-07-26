pipeline {
  agent any

  tools {
    gradle 'Gradle-6.2'
  }
  stages{
    stage("build"){
      steps{
        echo 'building the application...'
        nodejs('Node-22.5'){
          sh 'yarn install'
        }
      }
    }
    stage("test"){
      steps{
        echo 'testing the application'
      }
    }
    stage("deploy"){
      steps{
        echo 'deploying the application'
          sh './gradlew -v'
      }
    }
  }
}
