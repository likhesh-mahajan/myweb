currentBuild.displayName = "online-shopping-#"+currentBuild.number

pipeline{
    agent any
    
    environment{
        PATH = "/var/lib/jenkins/tools/hudson.tasks.Maven_MavenInstallation/maven3:$PATH"
    }
    stages{
        stage("Git Checkout"){
            steps{
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/likhesh-mahajan/myweb'
            }
        }
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
                sh "mv target/*.war target/myweb.war"
            }
        }
        // stage("deploy-dev"){
        //     steps{
        //         sshagent(['tomcat-new']) {
        //         sh """
        //             scp -o StrictHostKeyChecking=no target/myweb.war  ec2-user@172.31.5.176:/opt/tomcat8/webapps/
                    
        //             ssh ec2-user@172.31.5.176 /opt/tomcat8/bin/shutdown.sh
                    
        //             ssh ec2-user@172.31.5.176 /opt/tomcat8/bin/startup.sh
                
        //         """
        //     }
            
        //     }
        }
    }

