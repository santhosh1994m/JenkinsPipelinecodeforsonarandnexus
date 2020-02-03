
pipeline {
    agent any
    stages {
        stage(test) {
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
                 sh 'sudo git clone https://github.com/santhosh1994m/maventest.git'      
            }    
        }    
       stage('sleep') 
        {      
            steps 
            {      
              sh 'sleep 10'   
            }  
        }  
        stage('change the path'){
            steps {
                sh 'cd maventest'
            }
            }
        
        stage ('Build project') {
             steps {
              dir("/var/lib/jenkins/workspace/OFFICIALDECLARATIVEPIPELINE/maventest/"){
                sh 'mvn -B -DskipTests clean package'
              }
                  }
             } 
    }
    
}
