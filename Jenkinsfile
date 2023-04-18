pipeline {
  agent any
  environment {
	MULE_URI = "https://anypoint.mulesoft.com"
    DEPLOY_CREDS = credentials('deploy-anypoint-user')
    MULE_VERSION = "4.4.0"
    BG = "Cap4"
    BGID = "6a860bc2-7c16-4fc4-8c42-9a362133e5f9"
    WORKERS = "1"
    WORKERSIZE = "MICRO"
	APP_NAME = "customer-api"
	REGION= "us-east-2"
  }
  stages {
    stage('Deploiment CloudHub') { 
      environment {
        ENVIRONMENT= "Sandbox"
      }
      steps {
        sh 'mvn deploy -DmuleDeploy -Dmule.version="%MULE_VERSION%" -Danypoint.uri="%MULE_URI%" -Danypoint.username="%DEPLOY_CREDS_USR%" -Danypoint.password="%DEPLOY_CREDS_PSW%" -Dcloudhub.app="%APP_NAME%" -Dcloudhub.environment="%ENVIRONMENT%" -Dcloudhub.bg="%BG%" -Dcloudhub.bgid="%BGID%"  -Dcloudhub.worker="%WORKERS%" -Dcloudhub.workersize="%WORKERSIZE%" -Dcloudhub.region="%REGION%"'
      }
    }
  }
}

							