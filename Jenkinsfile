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
               deploy adapters: [tomcat9(credentialsId: '55f29bec-4fc7-41ba-927f-52f953c636e8', path: '', url: 'http://172.31.17.13:8080')], contextPath: 'test1', war: '**/*.war'
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
                deploy adapters: [tomcat9(credentialsId: '55f29bec-4fc7-41ba-927f-52f953c636e8', path: '', url: 'http://172.31.12.15:8080')], contextPath: 'prod1', war: '**/*.war'
            }
        }
    }
}

