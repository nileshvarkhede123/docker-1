pipeline{
    agent{
        label {
		
				label 'built-in'
				customWorkspace '/mnt/demo1'
				
		}
    }
    stages{
        stage("clean workspace"){
            steps{
                cleanWs()
                }
        }
        stage("checkout_scmcode"){
            steps{
                checkout scm
                }
        }
        stage("creating docker container on master"){
            steps{
                sh "sudo docker rm -f server-2"
                sh "sudo docker system prune -a -f"
                sh "sudo docker run -itdp 81:80 --name server-2 httpd"
                
                }
        }
        stage("copying index file in container"){
            steps{ 
	
                    sh  "chmod -R 777 /mnt/demo1/"
                    sh  "sudo docker cp /mnt/demo1/index.html server-2:/usr/local/apache2/htdocs"
                }
        }
    }
}
