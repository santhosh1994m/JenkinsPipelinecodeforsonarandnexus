
pipeline {
    agent any
tools {
    maven 'MAVEN_HOME'
    jdk 'JAVA_HOME11'
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
    steps {
        dir("/var/lib/jenkins/workspace/OFFICIALDECLARATIVEPIPELINE/maventest/"){// You can override the credential to be used
      sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:4.0.0.1744:sonar' +
      '-Dsonar.projectKey=santhoshhello' +
      '-Dsonar.host.url=https://35.229.112.150' + 
      '-Dsonar.login=7d2925cc122574560e4b94074d2cace3b821852b' +
      '-Dsonar.projectName=Simple Java project analyzed with the SonarQube Runner' +
      '-Dsonar.projectVersion=1.0' +
      '-Dsonar.sources=src' +
      '-Dsonar.language=java' +
      '-Dsonar.java.binaries=target' +
      '-Dsonar.sourceEncoding=UTF-8'
        }
    }
  }

       
    }
    
}
     
