node{
   stage('SCM Checkout'){
     git 'https://github.com/juned/DevOpsClassCodes'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'maven', type: 'maven'   
      sh "${mvnHome}/bin/mvn package"
   }

   stage('Test-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'maven', type: 'maven'
      sh "${mvnHome}/bin/mvn test"
   }
     
   stage('SonarQube Analysis') {
        def mvnHome =  tool name: 'maven', type: 'maven'
        withSonarQubeEnv('sonar') { 
          sh "${mvnHome}/bin/mvn sonar:sonar"
        }
    }
   
   stage('Email Notification'){
      mail bcc: '', body: '''Hi, Welcome to jenkins email alerts
      Thanks
      Juned''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'jkhan6722@gmail.com'
   }
}
