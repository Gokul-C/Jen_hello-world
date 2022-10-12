pipeline{
    agent any
    environment {
        PATH = "/opt/maven/bin:$PATH"
    }
    stages{
        stage ("clone code"){
            steps{
             git 'https://github.com/Gokul-C/Jen_hello-world.git'
            }
        }
        stage ("build code"){
            steps{
                sh "mvn clean install"
            }
        }
        stage ("deploy code to tomcat server"){
            steps{
                sshagent(['tomcat-ssh']) {
                    sh "scp ssh -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/maven/webapp/target/webapp.war ec2-user@65.1.95.114:/usr/share/tomcat/webapps"



                }
            }
        }
    }
}
