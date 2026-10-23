pipeline{
    agent{
        label{
            label "built-in"
            customWorkspace "/home/avi/giiitt"
        }
    }
    stages{
        stage('Check SSH') {
    steps {
        sh '''
            echo "Pipeline user:"
            whoami

            echo "Home directory:"
            echo "$HOME"

            echo "SSH directory:"
            ls -la "$HOME/.ssh" || true

            echo "SSH test:"
            ssh -o BatchMode=yes \
                -o StrictHostKeyChecking=yes \
                172.31.9.12 hostname
        '''
    }
}

        
        stage("clean"){
            steps{
                echo "cleaning"
            }
        }
        stage("build"){
            steps{
                echo "building"
                sh "ansible devlinux[0] -ba 'unzip /home/avi/tomcat/apache-tomcat-10.1.61.zip'"
                sh "ansible devlinux[0] -ba 'rm -rf /home/avi/tomcat/apache-tomcat-10.1.61.zip'"
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
