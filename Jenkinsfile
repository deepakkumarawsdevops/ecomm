
pipeline {                                      
    agent  { label 'docker_node_build'}

    environment 
    {
     DOCKERHUB_CREDENTIAl = credentials('docker-hub-login')

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
	stage('LogintoDockerHub')

	{
         steps{
           sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
          	  
	  }



	} 
	stage('Deploy'){

          steps {
             echo 'Deploying...'
	     sh 'docker push deepakkumarawsdevops/newapp:$BUILD_NUMBER'


	       
	              }


	            }

    }                                           

    }
        
