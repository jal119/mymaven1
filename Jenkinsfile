node('built-in')
{
    stage('ContinuousDownload')
    {
        git 'https://github.com/jal119/mymaven1.git'
    }
    stage('ContinuousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
       deploy adapters: [tomcat9(credentialsId: '8b5ec5a8-fd83-4ed5-b936-4661c4dfba53', path: '', url: 'http://54.175.103.120:8090/')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh '''java -jar /var/lib/jenkins/workspace/ScriptedPipeline/testing.jar
'''
    }
    stage('ContinuousDelivery')
    {
    input message: 'Need approvals from the DM!', submitter: 'Ibrahim'
   deploy adapters: [tomcat9(credentialsId: '8b5ec5a8-fd83-4ed5-b936-4661c4dfba53', path: '', url: 'http://44.203.186.180:9090/')], contextPath: 'prodapp', war: '**/*.war'

    }    
}    

