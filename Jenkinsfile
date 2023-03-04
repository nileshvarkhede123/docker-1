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
                sh "sudo docker rm server-1"
                sh "sudo docker syetem prune -a -f"
                sh "sudo docker run -itdp 80:80 --name server-1 httpd"
                
                }
        }
        stage("copying index file in container"){
            steps{
                    sh  "sudo chmod -R 777 $WORKSPACE/index.html"
                    sh  "sudo docker cp $WORKSPACE/index.html server-1:/usr/local/apache2/htdocs/"
                }
        }
    }
}
