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
                sh "ansible all -ba 'rm -rf tomcat/apache-tomcat-10.1.61'"
                sh "ansible all -ba 'rm -rf tomcat/apache-tomcat-10.1.61.zip'"
            }
        }
        stage("build"){
            steps{
                echo "building"
                sh "ansible all -bm dnf -a 'pkg=java-21-amazon-corretto.x86_64 state=present'"
                sh "ansible all -bm get_url -a 'url=https://dlcdn.apache.org/tomcat/tomcat-10/v10.1.61/bin/apache-tomcat-10.1.61.zip dest=tomcat'"
                sh "ansible all -ba 'unzip tomcat/apache-tomcat-10.1.61.zip -d tomcat'"
                sh "ansible all -ba 'chmod -R 777 /home/avi/tomcat'"
                sh "ansible all -bm copy -a 'src=/home/avi/giiitt/sample.war dest=tomcat/apache-tomcat-10.1.61/webapps'"
                sh "ansible all -ba '/home/avi/tomcat/apache-tomcat-10.1.61/bin/startup.sh'"
            }
        }
        stage("deploy"){
            steps{
                echo "deploying"
            }
        }
    }
}
