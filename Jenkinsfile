@Library('mylib')_
pipeline
{
    agent any
    stages
    {
        stage('ContDownload_Master')
        {
            steps
            {
                script
                {
                    cicd.gitDownload("maven")
                }
                
            }
        }
        stage('ContBuilt_Master')
        {
            steps
            {
                script
                {
                    cicd.mavenBuild()
                }
               
            }
        }
        stage('ContDeployment_Master')
        {
            steps
            {
                script
                {
                    cicd.tomcatDeploy("DeclarativePipelinewithSharedLibraries","172.31.18.129","testapp")
                }
              
            }
        }
        stage('ContTesting_Master')
        {
            steps
            {
                script
                {
                    cicd.gitDownload("FunctionalTesting")
                    cicd.runSelinium("DeclarativePipelinewithSharedLibraries")
                }
            }
               
    
        }
        stage('ContDelivery_Master')
        {
            steps
            {
                script
                {
                    cicd.tomcatDeploy("DeclarativePipelinewithSharedLibraries","172.31.23.21","prodapp")
                    
               

            }
        }
    }
}
}
