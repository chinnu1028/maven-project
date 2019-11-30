pipeline {
   def mvnHome
   stages{
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      steps{
      git url: 'https://github.com/chinnu1028/maven-project.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'M3'
      }
   }
   stage('Build') {
      // Run the maven build
      steps{
      withEnv(["MVN_HOME=$mvnHome"]) {
         if (isUnix()) {
            sh '"$MVN_HOME/bin/mvn" -Dmaven.test.failure.ignore clean package'
         } else {
            bat(/"%MVN_HOME%\bin\mvn" -Dmaven.test.failure.ignore clean package/)
         }
      }
      }
   }
   stage('Results') {
      steps{
      junit '**/target/surefire-reports/TEST-*.xml'
      archiveArtifacts 'target/*.jar'
   }
   }
   }
}
