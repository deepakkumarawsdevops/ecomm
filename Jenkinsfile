
pipeline {                                      
    agent any

    environment 
          {
          DOCKERHUB_CREDENTIAL= credential ('dockerid')
	          
	  }

    stages {



        // stage('SCM Checkout') 
	// {
        //steps{
        //    git 'https://github.com/deepakkumarawsdevops/ecomm.git'
	// }

	// }
         		
		
		
        stage('BuildDockerImage') {
            steps {                                                  
                echo 'Imageing..'
		sh 'docker build -t deepakkumarawsdevosp/newapp:$BUILD_NUMBER .'
		
		
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
        
