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
                sh "sudo docker run -itdp 80:80 --name server-1 httpd"
                sh "sudo docker run -itdp 81:80 --name server-2 httpd"
                sh "sudo docker run -itdp 82:80 --name server-3 httpd"
                      

                
                }
        }
        stage("copying index file in container"){
            steps{
                    sh  "chmod -R 777 $WORKSPACE/index.html"
                    sh  "sudo docker cp $WORKSPACE/index.html server-1:/usr/local/apache2/htdocs/"
                    sh  "chmod -R 777 $WORKSPACE/index.html"
                    sh  "sudo docker cp $WORKSPACE/index.html server-2:/usr/local/apache2/htdocs/"
                    sh  "chmod -R 777 $WORKSPACE/index.html"
                    sh  "sudo docker cp $WORKSPACE/index.html server-3:/usr/local/apache2/htdocs/"
                      

                }
        }
    }
}