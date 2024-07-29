pipeline {
  agent any
  environment {
    NEW_VERSION = '1.3.0'  
  }

  
  tools {
    gradle 'Gradle-6.2'
  }

  parameters {
    string(name: 'VERSION', defaultValue: '', description: 'version to deploy on prod)
    choice(name: 'VERSION', choices: ['1.1.0','1.2.0','1.3.0'], description: '')       
    booleanParam(name: 'executeTests', defaultValue: true, description: '')       
  }
  
  stages{
    stage("build"){
     //  when {
      //  expression {
      //    BRANCH_NAME =='dev' && CODE_CHANGES == true
      //  }
     // }
      
      steps{
        echo 'building the application...'
        echo "building version ${NEW_VERSION}"
        nodejs('Node-22.5'){
          sh 'yarn install'
        }
      }
    }
    stage("test"){
    //  when {
     //   expression {
       //   BRANCH_NAME =='dev' || BRANCH_NAME == 'master'
      //  }
    //  }
   when {
     expression {
       params.executeTests == true
     }
     
   }

      
      steps{
        echo 'testing the application'
      }
    }
    stage("deploy"){
      steps{
        echo 'deploying the application'
         echo "deploying version ${params.VERSION}"
        withCredentials([
          usernamePassword(credentials: 'server-credentials', usernameVariable: USER, passwordVariable: PWD)
        ]){
          sh "some script ${USER} ${PWD}  
        }
          sh './gradlew -v'
      }
    }
  }
}
