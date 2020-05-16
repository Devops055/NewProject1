node('master') 
{
   stage(' ContinuousDownload') 
   {
    git 'https://github.com/intelliqittrainings/maven.git'
   }
   stage(' ContinuousBuild') 
   {
    sh label: "",script:'mvn package'
   }
   stage(' ContinuousDeployment') 
   {
    sh label: "",script:'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.31.66:/var/lib/tomcat8/webapps/testapp.war'
   //sudo chmod o+w -R /var/lib/tomcat8/-->QA server
   //If multiple servers, just mention all server details like above.
   }
   stage(' ContinuousTest') 
   {
       git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
    sh label: "",script:'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
    //where automation scripts are present
   }
    stage(' ContinuousDelivery') 
   {
    input message:'waiting for approval from the DM',submitter:'srinivas'
    sh label: "",script:'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.19.198:/var/lib/tomcat8/webapps/prodapp.war'
   //sudo chmod o+w -R /var/lib/tomcat8/-- prodserver
    //If multiple servers, just mention all server details like above.
   }
}
