pipeline {
    agent any
    
    tools{
        maven 'Maven'
    }

    stages {
        stage ('Initialize') {
            steps {
             sh '''
                            echo "PATH = ${PATH}"
                            echo "M2_HOME = ${M2_HOME}"
                ''' 
            }
        }  
        stage('Build') {
            steps {
              
                    sh 'mvn clean package'
                        
               
            }
            
        }
        stage ('Deploy-To-Tomcat') {
            steps {
           sshagent(['tomcat']) {
                sh 'scp -o StrictHostKeyChecking=no target/WebApp.war ubuntu@65.1.132.28:/opt/tomcat/latest/webapps/webapp.war'
              }      
           }       
        }
    }
}
