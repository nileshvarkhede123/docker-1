pipeline{
    agent{
        label {
		
				label 'built-in'
				customWorkspace '/mnt/demo'
				
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
                sh "sudo docker rm -f server-1"
                sh "sudo docker system prune -a -f"
                sh "sudo docker run -itdp 80:80 --name server-1 httpd"
                
                }
        }
        stage("copying index file in container"){
            steps{
		    sh  "rm -rf /mnt/demo/"
                    sh  "chmod -R 777 /mnt/demo/"
                    sh  "sudo docker cp /mnt/demo/index.html server-1:/usr/local/apache2/htdocs"
                }
        }
    }
}
