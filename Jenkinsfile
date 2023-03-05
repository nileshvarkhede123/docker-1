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
                sh "sudo docker rm -f server-3"
                sh "sudo docker system prune -a -f"
                sh "sudo docker run -itdp 82:80 --name server-3 httpd"
                
                }
        }
        stage("copying index file in container"){
            steps{
                    sh  "rm -rf /mnt/*
		    sh  "chmod -R 777 /mnt/demo/"
                    sh  "sudo docker cp /mnt/demo/index.html server-3:/usr/local/apache2/htdocs"
                }
        }
    }
}
