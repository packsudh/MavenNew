@Library('newlibrary')_
pipeline
{
    agent any
    stages
        {
            stage ("Continuous Download")
            {
                steps
                {
                    script
                    {
                        cicd.newGit("https://github.com/packsudh/MavenNew.git")
                    }
                }
            }
        
            stage ('Continuous Build')
             {
                steps
                {
                    script
                    {
                        cicd.newMaven()
                    }
                }
            }
           stage ('Continuous Deployment')
            {
                steps
                {
                    script
                    {
                        cicd.newDeploy("DeclarativePipelineWithSharedLibraries","172.31.17.13","test1")
                    }
                }
            }
            
            stage ('Continuous Testing')
            {
                steps
                {
                    script
                    {
                        cicd.newGit("https://github.com/intelliqittrainings/FunctionalTesting.git")
                        cicd.runSelenium("DeclarativePipelineWithSharedLibraries")
                    }
                }
            }
            stage ('Continuous Delivery')
            {
                steps
                {
                    script
                    {
                        cicd.newDeploy("DeclarativePipelineWithSharedLibraries","172.31.12.15","prod1")
                    }
                }
            }
            
      }
}
