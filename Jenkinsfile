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
             deploy adapters: [tomcat9(credentialsId: '55f29bec-4fc7-41ba-927f-52f953c636e8', path: '', url: 'http://172.31.0.253:8080')], contextPath: 'prod1', war: '**/*.war'
            }
        }
    }    
  
}
