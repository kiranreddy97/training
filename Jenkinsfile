node('paytmnode'){
 
 properties([
    buildDiscarder(logRotator(numToKeepStr: '3')),
    pipelineTriggers([
        pollSCM('* * * * *')
    ])
])

 def mavenHome = tool name: 'maven3.6.1', type: 'maven'
 
 stage('CheckoutCode') {
 //git branch: 'master', credentialsId: '82478555-478a-4b62-900c-fcdedfa161a3', url: 'https://github.com/kiranreddy97/training.git'
  git 'https://github.com/kiranreddy97/training.git'
 }  
  
  stage('Build') {
 
    sh "${mavenHome}/bin/mvn clean package"
  
 }      
}
