
pipeline {                                      
    agent  { label "docker_node_build"}

    environment 
          {
          DOCKERHUB_CREDENTIAL= credential ('dockerid')
	          
	  }

    stages {



     
         		
		
		
        stage('BuildDockerImage') {
            steps {                                                  
                echo 'Imageing..'
		sh 'docker build -t deepakkumarawsdevops/newapp:$BUILD_NUMBER .'
		
		
            }
        }
        stage('ReleaseToDockerHub') {                                           
            steps {
                echo 'Releasing....'
		

            }
        }
	stage('Deploy'){

          steps {
             echo 'Deploying...'

	       
	              }


	            }

    }                                           

    }
        
