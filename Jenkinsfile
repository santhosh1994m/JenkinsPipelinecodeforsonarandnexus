
pipeline {
    agent any
    stages {
        stage(test) {
            steps {
            echo 'started'
            }
        }
        stage('chage path') { 
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
   
    
    }
    
}
