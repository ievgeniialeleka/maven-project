pipeline {
   agent any
	triggers{
		pollSCM('*/5 * * * *')
	}
   stages{
          stage ('Build') {
           steps {
            bat 'mvn clean package'
            }
		  post{
			  success{
				  echo 'Archiving...'
				  archiveArtifacts artifacts:'**/*.war'
			  }
		  }
          }
	   stage ('Deployments') {
		   parallel {
          stage ('Deploy to staging'){
           steps {
            bat 'copy  **/*.war /c/Users/ievge/Downloads/tomcat_staging/apache-tomcat-9.0.84/webapps'


            }
          }
	   stage ('Deploy to prod'){
           steps {
             bat 'copy /Y .\*\*.war "C:\Users\ievge\Downloads\tomcat_prod\apache-tomcat-9.0.84\webapps"'
            }
          }
	}
	}
    }
}
