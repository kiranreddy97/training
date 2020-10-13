node{
     
    stage('SCM Checkout'){
        git credentialsId: 'GIT_CREDENTIALS', url:  'https://github.com/kiranreddy97/training.git',branch: 'main'
    
    stage(" Maven Clean Package"){
      def mavenHome =  tool name: "maven", type: "maven"
      def mavenCMD = "${mavenHome}/bin/mvn"
      sh "${mavenCMD} clean package"
      
    } 
    
    
    stage('Build Docker Image'){
        sh 'docker build -t srikiranreddy/mavenapp .'
    }
    
    stage('Push Docker Image'){
        
      withCredentials([string(credentialsId: 'dockerpass', variable: 'dockerpassword')]) {
          sh "docker login -u srikiranreddy -p $dockerpassword"
        }
        sh 'docker push srikiranreddy/mavenapp'
 }
 stage('run docker images as container '){
     sh 'docker run -d -p 9091:8080 --name tomcatjenkins srikiranreddy/mavenapp '
 }
}
}
