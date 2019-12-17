pipeline {
    agent any
    environment {
        // adding maven to the path
        PATH = "${PATH}:${tool name: 'maven3', type: 'maven'}/bin"
    }
    stages {
        stage ('SCM checkout'){
            steps {
                git credentialsId: 'git-1', 
                url: 'https://github.com/git212/jenkins',
                branch: 'master'
            }
        }
        stage ('Maven build'){
            steps {
                sh "mvn clean package"
                
            }
        }
        stage ('Deploy dev'){
            steps{
                 sshagent(['tomcat-dev']) {
                    // stop tomcat
                    sh "ssh -o StrictHostKeyChecking=no ec2-user@18.217.237.212 /tomcat8/bin/shutdown.sh"
                    // copy war file to remote tomcat
                    sh "scp target/6pmwebapp.war  ec2-user@18.217.237.212:/tomcat8/webapps/"
                    // start tomcat
                    sh "ssh ec2-user@18.217.237.212 /tomcat8/bin/startup.sh"
                }
            }
        }
        post {
            success {
                echo "sending email"
            }
        }
    }
       
}
