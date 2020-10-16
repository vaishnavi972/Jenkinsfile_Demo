node('master') 
{
    stage('ContinuousDownload') 
    {
        git 'https://github.com/vaishnavi972/maven.git'
    }
    stage('ContinuousBuild') 
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment') 
    {
        sh 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.87.90:/var/lib/tomcat8/webapps/testapp.war'
    }
    stage('ContinuousTesting') 
    {
        git 'https://github.com/vaishnavi972/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
    }
    stage('ContinuousDelivery') 
    {
        sh 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.92.230:/var/lib/tomcat8/webapps/prodapp.war'
    }
}
