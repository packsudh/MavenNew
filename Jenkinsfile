pipeline
{
    agent any
    stages
    {
        stage ("ContinousDownload")
        {
            steps
            {
                git 'https://github.com/packsudh/MavenNew.git'
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
               sh 'scp /var/lib/jenkins/workspace/DeclarativePipelineNew/webapp/target/webapp.war ubuntu@172.31.17.13:/var/lib/tomcat9/webapps/test1.war'
            }
        }
        stage ("ContinousTesting")
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipelineNew/testing.jar'
            }
        }
        stage ("ContinuousDelivery")
        {
            steps
            {
               sh 'scp /var/lib/jenkins/workspace/DeclarativePipelineNew/webapp/target/webapp.war ubuntu@172.31.12.15:/var/lib/tomcat9/webapps/prod1.war'
            }
        }
    }
}

