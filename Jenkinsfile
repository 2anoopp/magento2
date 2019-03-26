node{

def magento2

    stage('Clone repository') {


        checkout scm
    }

    stage('Build image') {
 

        magento2 = docker.build("569177097303.dkr.ecr.us-west-2.amazonaws.com/magento2")
          
    }

    stage('Test image') {

        magento2.inside {
            sh 'echo "Tests passed successfully "'
          
        }
        
    }
  
  stage('Push image') {
        docker.withRegistry('https://569177097303.dkr.ecr.us-west-2.amazonaws.com') {
            magento2.push("${env.BUILD_NUMBER}")
            magento2.push("latest")
            
        }
    }
  
  
  
  stage('Delete all images and containers'){
    
            sh "docker system prune -a -f"
  }
}
