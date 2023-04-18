pipeline {
  agent any
  environment {
    //adding a comment for the commit test
	
    DEPLOY_CREDS = credentials('deploy-anypoint-user')
    MULE_VERSION = '4.4.0'
    BG = "None"
    WORKER = "MICRO"
	APP_NAME = "customer-api"
  }
  stages {
    stage('Deploiment CloudHub') { 
      environment {
        ANYPOINT_CREDENTIALS = credentials('deploy-anypoint-user')
      }
      steps {
        sh 'mvn deploy -DmuleDeploy -Dmule.version="%MULE_VERSION%" -Danypoint.username="%DEPLOY_CREDS_USR%" -Danypoint.password="%DEPLOY_CREDS_PSW%" -Dcloudhub.app="%APP_NAME%" -Dcloudhub.environment="%ENVIRONMENT%" -Dcloudhub.bg="%BG%" -Dcloudhub.worker="%WORKER%"'
      }
    }
  }
}