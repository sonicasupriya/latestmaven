pipeline
{
    agent any
    stages
    {
        stage('ContDownload')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('ContBuilt')
        {
            steps
            {
               sh 'mvn package'
            }
        }
        stage('ContDeployment')
        {
            steps
            {
	      deploy adapters: [tomcat9(credentialsId: 'f0260a0b-9b35-4202-910d-d9e6d7d141cb', path: '', url: 'http://172.31.18.129:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
        stage('ContTesting')
        {
            steps
            {
               git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
               sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline/testing.jar'
            }
        }
        stage('ContDelivery')
        {
            steps
            {
               	        deploy adapters: [tomcat9(credentialsId: 'f0260a0b-9b35-4202-910d-d9e6d7d141cb', path: '', url: 'http://172.31.23.21:8080')], contextPath: 'prodapp', war: '**/*.war'


            }
        }
    }
}
