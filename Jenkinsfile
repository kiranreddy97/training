node{
     
    stage('SCM Checkout'){
        git credentialsId: 'GIT_CREDENTIALS', url:  'https://github.com/kiranreddy97/training.git',branch: 'main'
    
    stage(" Maven Clean Package"){
      def mavenHome =  tool name: "maven", type: "maven"
      def mavenCMD = "${mavenHome}/bin/mvn"
      sh "${mavenCMD} clean package"
      
    } 
    
    
    stage('Build Docker Image'){
        sh 'docker build -t docker.io/srikiranreddy/mavenapp:1 .'
    }
    
    stage('Push Docker Image'){
        
 withCredentials([usernamePassword(credentialsId: '3f123fe3-ce62-4f7d-806a-943d782f0d94', passwordVariable: 'Amma@1234', usernameVariable: 'srikiranreddy')]) {
    // some block
}
        sh 'docker push docker.io/srikiranreddy/mavenapp:1'
 }
 stage('run docker images as container '){
     sh 'docker run -d -p 9091:8080 --name tomcatjenkins docker.io/srikiranreddy/mavenapp '
 }
}
}
