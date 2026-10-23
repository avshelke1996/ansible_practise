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
                sh "ansible qalinux[0] -ba 'rm -rf tomcat/apache-tomcat-10.1.61'"
                sh "ansible qalinux[0] -ba 'rm -rf tomcat/apache-tomcat-10.1.61.zip'"
            }
        }
        stage("build"){
            steps{
                echo "building"
                sh "ansible qalinux[0] -bm get_url -a 'url=https://dlcdn.apache.org/tomcat/tomcat-10/v10.1.61/bin/apache-tomcat-10.1.61.zip dest=tomcat'"
                sh "ansible qalinux[0] -ba 'unzip tomcat/apache-tomcat-10.1.61.zip -d tomcat'"
                sh "ansible qalinux[0] -ba 'chmod -R 777 /home/avi/tomcat'"
                sh "ansible qalinux[0] -bm copy -a 'src=/home/avi/giiitt/sample.war dest=tomcat/apache-tomcat-10.1.61/webapps'"
                sh "ansible qalinux[0] -ba '/home/avi/tomcat/apache-tomcat-10.1.61/bin/startup.sh'"
            }
        }
        stage("deploy"){
            steps{
                echo "deploying"
            }
        }
    }
}
