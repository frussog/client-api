pipeline {
  agent any
  environment {
    //adding a comment for the commit test
    DEPLOY_CREDS = credentials('deploy-anypoint-frussog')    
    BG = "Test"      
  }
  stages {
    stage('Build') {
      steps {
            bat 'mvn -B -U -e -V clean -DskipTests package'
      }
    }



     stage('Deploy Development') {
      environment {
        ENVIRONMENT = 'Sandbox'
        APP_NAME = 'client-service-api-sandbox'
      }
      steps {
      
			bat 'mvn -U -V -e -B -DskipTests deploy -DmuleDeploy -Dapp.runtime=4.3 -Danypoint.username="%DEPLOY_CREDS_USR%" -Danypoint.password="%DEPLOY_CREDS_PSW%" -Dtarget=retail-revamp-sandbox -Dtarget.type=server  -Denvironment=Sandbox -Denv=Sandbox'            
      }      
    }
  }  
}