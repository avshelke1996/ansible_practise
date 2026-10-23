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
                sh "ansible devlinux[0] -ba 'chmod -R 777 /home/avi/tomcat/'"
                sh "ansible devlinux[0] -bm copy -a 'src=/home/avi/giiitt/sample.war dest=tomcat/apache-tomcat-10.1.61/webapps'"
                sh "ansible devlinux[0] -ba '/home/avi/tomcat/apache-tomcat-10.1.61/bin/startup.sh'"
            }
        }
        stage("deploy"){
            steps{
                echo "deploying"
            }
        }
    }
}
