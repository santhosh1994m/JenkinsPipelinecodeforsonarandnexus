
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
        
       stage ('Build') {
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true package' 
            }
       }
        
   
    
    }
    
}
