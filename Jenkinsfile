node('master')
{
   stage('ContinuousDownload')
   {
      git 'https://github.com/Devops055/NewProject1.git'
   }
   stage('ContinuousBuild')
   {
       sh label: '', script: 'mvn package'
   }
         
}
