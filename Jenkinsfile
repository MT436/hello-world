node{ 
   stage("SonarQube analysis") {
          node {
              withSonarQubeEnv('sonar') {
                 sh 'mvn /var/lib/jenkins/workspace/hello-world/pom.xm clean package sonar:sonar'
//it creates sonar project if we want we can add quality using snippet
              }    
          }
      }
    
    sleep 3
    stage 'deploy'
   deploy adapters: [tomcat9(credentialsId: 'TOMcat', path: '', url: 'http://172.31.35.76:8082/')], contextPath: null, war: '**/*.war'
 // now we are using private ip for tomcat deploy if we are using public ip we need to generate the above script everytime  
}
