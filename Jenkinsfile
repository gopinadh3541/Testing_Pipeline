node{
   stage('Checkout')
    {
        checkout scm
    }
    stage('Clean')
    {
		withMaven(maven: 'ECD Maven 3.3.9 Linux')
		{
        sh "mvn -f Pipeline_test/pom.xml clean"
		}
    }
    stage('Unit Test')
    {
		withMaven(maven: 'ECD Maven 3.3.9 Linux')
		{
		sh "mvn -f Pipeline_test/pom.xml test"
		}
    }
   
   
    stage('Packaging')
    {
        withMaven(maven: 'ECD Maven 3.3.9 Linux')
		{
		sh "mvn -f Pipeline_test/pom.xml test"
		}
    }
   stage('Deploy?')
    {
       input 'Proceed to Deploy?'
    }
   stage('Deploy')
   {
   
	withMaven(maven: 'ECD Maven 3.3.9 Linux')
	{
		//sh "mvn -f Pipeline_test/pom.xml deploy"
		sh "mvn -f Pipeline_test/pom.xml package -Ddeploy.to.weblogic -Ddeploy.for.weblogic"
	}
   
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

    
 
