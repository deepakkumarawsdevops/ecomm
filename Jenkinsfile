
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
	      def dockerRun = 'docker run -dt --name app -p 8080:80 deepakkumarawsdevops/newapp:$BUILD_NUMBER'
	      sh 'ssh -o StrictHostKeyChecking=no ec2-user:18.133.195.231 ${dockerRun}'
	      //sh 'docker container run -dt -name app -p 8080:80 deepakkumarawsdevops/newapp:$BUILD_NUMBER'
           }
        }
    }



    }                                           

    }
        
