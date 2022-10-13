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
                sshagent(credentials : ['tomcat-server']) {
                    //sh "scp ssh -o StrictHostKeyChecking=no  /var/lib/jenkins/workspace/maven/webapp/target/webapp.war ec2-user@ec2-43-205-118-71.ap-south-1.compute.amazonaws.com:/usr/share/tomcat/webapps"
                    sh 'ssh -i ~/.ssh/tomcat.pem -o StrictHostKeyChecking=no ec2-user@ec2-43-205-118-71.ap-south-1.compute.amazonaws.com'
                    sh 'scp   /var/lib/jenkins/workspace/Tomcat-deployment/webapp  ec2-user@ec2-43-205-118-71.ap-south-1.compute.amazonaws.com:/usr/share/tomcat/webapps'



                }
            }
        }
    }
}
