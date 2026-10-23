pipeline{
    agent{
        label{
            label "built-in"
            customWorkspace "/home/avi/giiitt"
        }
    }
    stages{
        stage("clean"){
            steps{
                echo "cleaning"
            }
        }
        stage("build"){
            steps{
                echo "building"
                sh "ansible devlinux[0] -ba 'unzip /home/avi/tomcat/apache-tomcat-10.1.60.zip'"
                sh "ansible devlinux[0] -ba 'rm -rf /home/avi/tomcat/apache-tomcat-10.1.60.zip'"
                sh "ansible devlinux[0] -ba 'chmod -R 777 /home/avi/tomcat/'"
                sh "ansible devlinux[0] -bm copy -a 'src=sample.war dest=/home/avi/tomcat/apache-tomcat-10.1.60/webapps/'"
                sh "ansible devlinux[0] -bm shell -a 'cd /home/avi/tomcat/apache-tomcat-10.1.60/bin && ./startup.sh'"
            }
        }
        stage("deploy"){
            steps{
                echo "deploying"
            }
        }
    }
}
