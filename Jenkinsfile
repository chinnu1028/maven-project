pipeline {
   agent any

   tools {
  maven 'maven'
}

   
   stages{
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      steps{
      git url: 'https://github.com/chinnu1028/maven-project.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      }
   }
   stage('Build') {
      // Run the maven build

      steps{
         bat 'mvn -Dmaven.test.failure.ignore clean package'
         
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
