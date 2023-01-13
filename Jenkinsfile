pipeline
{
    agent any
    stages
    {
        stage ("ContinousDownload")
        {
            steps
            {
              git 'https://github.com/packsudh/maven.git' 
            }
        }
        stage ("ContinousBuild")
        {
            steps
            {
              sh 'mvn package'
            }
        }
         stage ("ContinousDeployment")
        {
            steps
            {
              sh 'scp /var/lib/jenkins/workspace/DeclarativePipeline1/webapp/target/webapp.war ubuntu@52.53.210.40:/var/lib/tomcat9/webapps/testapp.war'
            }
        }
        stage ("ContinousTesting")
        {
            steps
            {
              git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
              sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        stage ("ContinousDelivery")
        {
            steps
            {
             sh '/var/lib/jenkins/workspace/DeclarativePipeline1/webapp/target/webapp.war ubuntu@50.18.232.121:/var/lib/tomcat9/webapps/prodapp.war'
            }
        }
    }    
  
}
