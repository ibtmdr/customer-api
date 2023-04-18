pipeline {
  agent any
  environment {
    //adding a comment for the commit test
	MULE_URI = "https://anypoint.mulesoft.com"
    DEPLOY_CREDS = credentials('deploy-anypoint-user')
    MULE_VERSION = '4.4.0'
    BG = "None"
    BGID = "9f51add0-4db7-4281-ba02-a07dc471768f"
    WORKERS = "1"
    WORKERSIZE = "MICRO"
	APP_NAME = "customer-api"
	REGION= "us-east-2"
  }
  stages {
    stage('Deploiment CloudHub') { 
      environment {
        ANYPOINT_CREDENTIALS = credentials('deploy-anypoint-user')
        ENVIRONMENT=Sandbox
      }
      steps {
        sh 'mvn deploy -DmuleDeploy -Dmule.version="%MULE_VERSION%" -Danypoint.uri="%MULE_URI%"  "-Danypoint.username="%DEPLOY_CREDS_USR%" -Danypoint.password="%DEPLOY_CREDS_PSW%" -Dcloudhub.app="%APP_NAME%" -Dcloudhub.environment="%ENVIRONMENT%" -Dcloudhub.bg="%BG%" -Dcloudhub.worker="%WORKERS%" -Dcloudhub.workersize="%WORKERSIZE%" -Dcloudhub.region="%REGION%" '
      }
    }
  }
}

							    <environment>${cloudhub.environment}</environment>
							    <applicationName>${cloudhub.app}</applicationName>
							    <workers>${cloudhub.workers}</workers>
							    <workerType>${cloudhub.worker}</workerType>