node('master')
{
    stage('ContinuousDownload') 
    {
        git 'https://github.com/selenium-saikrishna/maven-july.git'
    }
    stage('ContnuousBuild')
    {
        sh label: '', script: 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.86.177:/var/lib/tomcat8/webapps/testenv.war'
    }
    stage('ContunuousTesting')
    {
        git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
        sh label: '', script: '''java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar
'''
    }
    stage('ContinuousDelivery')
    {
         sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.84.219:/var/lib/tomcat8/webapps/prodenv.war' 
    }
    
    
}

