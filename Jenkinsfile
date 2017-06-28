node {
   def master
   stage('Preparation') { 
      
        checkout scm
     
   }
   stage('Create Docker Image') {
      
      sh 'docker-compose up -d')
    }
          
   stage('Run Tests') {
    try {
              sh "docker exec -t '*_helloworld_nginx_*' curl -s http://localhost/ | grep Welcome | wc -l | tr -d '\n' > ${test} " 
              if (test == 0){
                   echo "Bundle loaded"
              }
              else {
                echo "Bundle not loaded"
                currentBuild.result = 'FAILURE'
              }

          } catch (error)   
   }
   
   }