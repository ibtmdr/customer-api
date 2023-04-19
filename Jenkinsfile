pipeline {
  agent any
  environment {
		DEPLOY_CREDS = credentials('deploy-anypoint-user')
	    MULE_VERSION = "4.4.0"
	    BG = "Cap4"
	    BGID = "6a860bc2-7c16-4fc4-8c42-9a362133e5f9"
	    WORKERS = "1"
	    WORKERSIZE = "Micro"
		APP_NAME = "customer-api"
		REGION= "us-east-2"
  } 
  stages {
    stage('Build') {
      steps {
          sh "mvn clean install"
      }
    }

    stage('Deploiment CloudHub') { 
    
      steps {
          sh "mvn -e -X deploy -DmuleDeploy -Dmule.version=${env.MULE_VERSION} -Danypoint.username=${DEPLOY_CREDS_USR} -Danypoint.password=${DEPLOY_CREDS_PSW} -Dcloudhub.app=${env.APP_NAME}-${env.ENVIRONMENT.toLowerCase()} -Dcloudhub.environment=${env.ENVIRONMENT} -Dcloudhub.bg=${env.BG} -Dcloudhub.bgid=${env.BGID}  -Dcloudhub.worker=${env.WORKERS} -Dcloudhub.workersize=${env.WORKERSIZE} -Dcloudhub.region=${env.REGION}"
      }
    }
  }
}

							