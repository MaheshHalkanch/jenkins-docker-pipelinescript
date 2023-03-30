pipeline {
    agent any  
         
        stages{
	stage('Clone Repo'){
            steps{
		 checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'b02b81e0-ffde-4d4e-bbde-27de576dc6a6', url: 'https://github.com/MaheshHalkanch/jenkins-docker-example.git']]])
             bat 'mvn clean package'
             echo "build successfully _now THIS SCRIPT IS BEING USED FROM git"
                
            }
         }
         stage("build docker image"){
             steps{
                 script{
                     bat 'docker build -t maheshhalkanche/jenkins-docker-example:latest . '
                 }
             }
         }
         stage('push image to docker hub'){
             steps{
                 script{
                      withCredentials([string(credentialsId: 'maheshhalkanche', variable: 'docker_hub')]) {
                      bat 'docker login -u maheshhalkanche -p M@hesh111 '
                      
                      bat 'docker push maheshhalkanche/jenkins-docker-example:latest'
}
                 }
             }
         }
         
	     
    }
}
        
    
