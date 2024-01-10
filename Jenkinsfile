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
    }
}
