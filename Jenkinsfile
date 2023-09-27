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
        stage('ContBuild')
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
               deploy adapters: [tomcat9(credentialsId: 'd34cc189-30e7-4891-8114-9d9d18fcfa89', path: '', url: 'http://172.31.2.91:8080')], contextPath: 'test1', war: '**/*.war'
            }
        }
        stage('ContTesting')
        {
            steps
            {
               git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
               sh 'java -jar /var/lib/jenkins/workspace/declarativePipeline1/testing.jar'
            }
        }
        stage('ContDelivery')
        {
            steps
            {
                 deploy adapters: [tomcat9(credentialsId: 'd34cc189-30e7-4891-8114-9d9d18fcfa89', path: '', url: 'http://172.31.14.231:8080')], contextPath: 'prod1', war: '**/*.war'
            }
        }
       
    }
    
}

