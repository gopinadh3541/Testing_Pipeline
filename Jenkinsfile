node('master'){
   stage('Checkout')
    {
        checkout scm
    }
    stage('Clean')
    {
	
        bat "mvn -f Pipeline_test/pom.xml clean"
	
    }
    stage('Unit Test')
    {
		
		
		bat "mvn -f Pipeline_test/pom.xml test"
		
    }
   
   
    stage('Packaging')
    {
        
		bat "mvn -f Pipeline_test/pom.xml install"
	
    }
   stage('Deploy?')
    {
       input 'Proceed to Deploy?'
    }
   stage('Deploy')
   {
   
	withMaven(maven: 'ECD Maven 3.3.9 Linux')
	   {
		bat "mvn -f Pipeline_test/pom.xml deploy"
	   }
	   //withCredentials([usernamePassword(credentialsId: 'By_Login', passwordVariable: 'wl.password', usernameVariable: 'wl.user')]) {
		//bat "mvn -f Pipeline_test/pom.xml package -Ddeploy.to.weblogic -Ddeploy.for.weblogic"
	   //}
	
   
     // bat 'mvn package -Ddeploy.to.weblogic -Ddeploy.for.weblogic'
   }
   
    /*stage('Deploy')
    {
        
     parallel firstBranch: {
       build job: 'New_appl', parameters: [string(name: 'DEPLOYMENT_ARTIFACT_PATH', value: 'C:\\jenkins_installpath\\workspace\\BankAppl\\target'), string(name: 'DEPLOYMENT_ARTIFACT_NAME', value: 'BankExample')]
    }, secondBranch: {
        build job: 'Tomcat_appl', parameters: [string(name: 'DEPLOYMENT_ARTIFACT_PATH', value: 'C:\\jenkins_installpath\\workspace\\BankAppl\\target'), string(name: 'DEPLOYMENT_ARTIFACT_NAME', value: 'BankExample')]
    },
    failFast: true
    
    }*/
}

    
 
