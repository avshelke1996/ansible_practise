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
                sh "ansible devlinux[0] -bm shell -a 'cd /home/avi/tomcat && wget https://dlcdn.apache.org/tomcat/tomcat-10/v10.1.61/bin/apache-tomcat-10.1.61.zip'"
                sh "ansible devlinux[0] -ba 'chmod -R 777 /home/avi/tomcat/'"
                sh "ansible devlinux[0] -bm copy -a 'src=/home/avi/giiitt/sample.war dest=/home/avi/tomcat/apache-tomcat-10.1.61/webapps/'"
                sh "ansible devlinux[0] -bm shell -a 'cd /home/avi/tomcat/apache-tomcat-10.1.61/bin && ./startup.sh'"
            }
        }
        stage("deploy"){
            steps{
                echo "deploying"
            }
        }
    }
}
