
pipeline {
    agent any
tools {
    maven 'MAVEN_HOME'
    jdk 'JAVA_HOME'
    git 'GIT_HOME'
                }
    stages {
        stage(Start) {
            steps {
            echo 'started'
            }
        }
        stage('remove the old path') { 
            steps 
            {          
                  sh 'if [ -d maventest ]; then sudo rm -rf maventest; fi'   
            }        
             }     
        stage('git clone') 
        {         
            steps 
            {  
                 sh 'sudo git clone https://github.com/santhosh1994m/maventest.git && sudo chown jenkins:jenkins /var/lib/jenkins/workspace/OFFICIALDECLARATIVEPIPELINE/maventest/'      
            }    
        }    
       stage('sleep') 
        {      
            steps 
            {      
              sh 'sleep 10'   
            }  
        }       
             
          stage('Build') {
            steps {
                dir("/var/lib/jenkins/workspace/OFFICIALDECLARATIVEPIPELINE/maventest/"){
                sh 'mvn -B -DskipTests clean package'
                }
            }
        }
        
  stage('SonarQube analysis') {
    withSonarQubeEnv(credentialsId: '7d2925cc122574560e4b94074d2cace3b821852b', installationName: 'sonarqube_home') { // You can override the credential to be used
      sh 'mvn sonar:sonar' +
      '-Dsonar.projectKey=santhoshhello' +
      '-Dsonar.host.url=https://35.229.112.150' + 
      '-Dsonar.login=7d2925cc122574560e4b94074d2cace3b821852b'
    }
  }
}
       
    }
    
}
     
