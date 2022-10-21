pipeline{
    agent {
        label "ansible-server"
    }
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
                sh "cp /home/ansadmin/workspace/Deploytocontainer/webapp/target/*.war  /opt/docker"
            }
        }
        


            
            
        
    }
}
