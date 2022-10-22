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
                
            }
        }
        
        stage ("copy artifacts to destination"){
            steps{
                sh  "cp /home/ansadmin/workspace/Deploytocontainer/webapp/target/*.war  /opt/docker"
            }
        }

        stage ("build , tag and push image to dockerhub"){
            steps{
                sh "cd /opt/docker"
                sh "ansible-playbook -i hosts /opt/docker/playbook.yml"
            }
        }    

            
            
        
    }
}
