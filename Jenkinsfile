
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
                 sh 'sudo git clone https://github.com/santhosh1994m/maventest.git && sudo chown jenkins:jenkins /var/lib/jenkins/workspace/OFFICIALDECLARATIVEPIPELINE/maventest/ && sudo chown jenkins:jenkins /var/lib/jenkins/workspace/OFFICIALDECLARATIVEPIPELINE/maventest/*'      
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
      tools {
                   jdk 'JAVA_HOME11'
                }
    steps {
        withSonarQubeEnv('Sonarqube_home'){
        dir("/var/lib/jenkins/workspace/OFFICIALDECLARATIVEPIPELINE/maventest/"){// You can override the credential to be used
      sh 'var/lib/jenkins/tools/hudson.plugins.sonar.SonarRunnerInstallation/sonarqube/bin/sonar-scanner ' +
      '-Dsonar.projectKey=santhoshhello ' +
      '-Dsonar.projectVersion=1.0 ' +
      '-Dsonar.sources=src ' +
      '-Dsonar.language=java ' +
      '-Dsonar.java.binaries=target ' +
      '-Dsonar.sourceEncoding=UTF-8 '
        }
    }
  }
  }

       
    }
    
}
     
