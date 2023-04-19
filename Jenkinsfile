pipeline {
  agent any
  environment {
		DEPLOY_CREDS = credentials('deploy-anypoint-user')
	    MULE_VERSION =4.4.0
	    BG =Cap4
	    BGID =6a860bc2-7c16-4fc4-8c42-9a362133e5f9
	    WORKERS = "1"
	    WORKERSIZE = "Micro"
		APP_NAME = "customer-api"
		REGION= "us-east-2"
		ENVIRONMENT= "Sandbox"
  } 
  stages {
    stage('Build') {
      steps {
          sh "mvn clean -DskipTests package"
      }
    }

    stage('Test') {
      steps {
          sh "mvn test"
      }
    }
    stage('Deploiment CloudHub to Sandbox') { 
      environment {
          ENVIRONMENT= "Sandbox"
      }
      steps {
          sh "mvn -e -X clean package deploy -DmuleDeploy -Dmule.version=4.4.0  -Danypoint.username=mdrIbtissam  -Danypoint.password=Ibtissam@12345  -Dcloudhub.app=customer-api-123  -Dcloudhub.environment=Sandbox  -Dcloudhub.bg=Cap4  -Dcloudhub.workers=1  -Dcloudhub.workersize=Micro  -Dcloudhub.bgid=6a860bc2-7c16-4fc4-8c42-9a362133e5f9 -Dcloudhub.region=us-east-2"
      }
    }
  }
}

							