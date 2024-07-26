pipeline {
  agent any

  tools {
    gradle 'Gradle-8.9'
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
        withGradle(){
          sh './gradlew -v'
        }
      }
    }
  }
}
