
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
         steps('Sonar') { 
          sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.3.0.603:sonar ' + 
          '-f all/pom.xml ' +
          '-Dsonar.projectKey=hellosanthoshkumar:all:master ' +
          '-Dsonar.login=admin ' +
          '-Dsonar.password=Fq7BHvtacgUq' +
          '-Dsonar.language=java ' +
          '-Dsonar.sources=src ' +
          '-Dsonar.java.binaries=target' +
          '-Dsonar.sourceEncoding=UTF-8'
        }
    }
       
        
    }
    
}
     
