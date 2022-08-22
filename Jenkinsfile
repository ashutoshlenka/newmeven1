node('built-in')
{
   stage('ContineousDownload')
   {
       git 'https://github.com/intelliqittrainings/maven.git'
   }
   stage('ContineousBuild')
   {
       sh 'mvn package'
   }
   stage('ContineousDeployment')
   {
       deploy adapters: [tomcat9(credentialsId: 'f96bf44d-088a-467a-b15b-6f0a7362828e', path: '', url: 'http://172.31.95.137:8080')], contextPath: 'mytestapp', war: '**/*.war'
   }
   stage('ContineousTesting')
   {
       git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
       sh 'java -jar /home/ubuntu/.jenkins/workspace/scriptedpipeline1/testing.jar'
   }
   stage('ContineousDelivery')
   {
       input message: 'Need approval from the DM!', submitter: 'srinivas'
       deploy adapters: [tomcat9(credentialsId: 'f96bf44d-088a-467a-b15b-6f0a7362828e', path: '', url: 'http://172.31.81.113:8080')], contextPath: 'myprodapp', war: '**/*.war'
   }
}
