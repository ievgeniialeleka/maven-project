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
				  archiveArtifacts artifacts:'**/target/*.war'
			  }
		  }
          }
	   stage ('Deployments') {
		   parallel {
          stage ('Deploy to staging'){
           steps {
            bat 'xcopy /s /y "C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\mvn_pipeline_as_code\\webapp\\target\\webapp.war" "C:\\Users\\ievge\\Downloads\\tomcat_staging\\apache-tomcat-9.0.84\\webapps"'


            }
          }
	   stage ('Deploy to prod'){
           steps {
             bat 'xcopy /s /y "C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\mvn_pipeline_as_code\\webapp\\target\\webapp.war" "C:\\Users\\ievge\\Downloads\\tomcat_prod\\apache-tomcat-9.0.84\\webapps"'
            }
          }
	}
	}
    }
}
