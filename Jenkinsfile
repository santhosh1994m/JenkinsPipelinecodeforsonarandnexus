
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
            steps{
            withSonarQubeEnv('sonarqube') { 
          sh 'sonar.projectKey=hellosanthoshkumar:all:master ' +
          'sonar.login=admin ' +
          'sonar.password=Fq7BHvtacgUq' +
          'sonar.language=java ' +
          'sonar.sources=src ' +
          'sonar.java.binaries=target' +
          'sonar.sourceEncoding=UTF-8'
        }
    }
        }
       
        
    }
    
}
     
