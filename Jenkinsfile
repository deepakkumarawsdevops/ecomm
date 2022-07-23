
pipeline {                                      
    agent  { label 'docker_node_build'}

    environment 
    {
     DOCKERHUB_CREDENTIALS = credentials('docker-hub-login')

    }


    stages {
	

           stage('BuildDockerImage') {
            steps {                                                  
                echo 'Imageing..'
		sh 'docker build -t deepakkumarawsdevops/newapp:$BUILD_NUMBER .'
		
		
            }
        }
        
	stage('LogintoDockerHub')

	{
         steps{
           sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
          	  
	  }



	} 
	stage('ReleaseToDockerHub'){

          steps {
             echo 'Releasing...'
	     sh 'docker push deepakkumarawsdevops/newapp:$BUILD_NUMBER'
                 
              }

            }
         stage('Deployment') {
            steps {
                echo 'Deploying....'
              
              sshagent(['76501201-7416-49db-af7d-69284a97283a']) {
	      
	      
	      sh 'docker container run -dt --name app1 -p 8080:80 deepakkumarawsdevops/newapp:$BUILD_NUMBER'
           }
        }
    }



    }                                           

    }
        
