pipeline {
   agent any
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
          stage ('Deploy'){
           steps {
            echo "Deploy step..."
            }
          }
    }
}
