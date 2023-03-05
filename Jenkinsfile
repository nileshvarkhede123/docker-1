pipeline{
    agent any
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
                    sh  "chmod -R 777 /root/.jenkins/workspace"
                    sh  "sudo docker cp /root/.jenkins/workspace server-1:/usr/local/apache2/htdocs"
                }
        }
    }
}
