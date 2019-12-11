pipeline {
    agent any
    environment {
        PATH = "${PATH}:${tool name: 'maven1', type: 'maven'}/bin"
    }
    stages {
        stage('SCM checkout'){
            steps{
                git credentialsId: 'git-1', url: 'https://github.com/git212/jenkins'
            }
        }
        stage('Maven Build'){
            steps {
                sh 'mvn clean package'
            }
        }
        stage ('Deploy Dev'){
            steps {
                sshagent(['tomcat-dev']) {
                    // stop tomcat
                    sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.40.190 /opt/tomcat8/bin/shutdown.sh"
                    // copy war file to remote tomcat
                    sh "scp target/6pmwebapp.war  ec2-user@172.31.40.190:/opt/tomcat8/webapps/"
                    // start tomcat
                    sh "ssh ec2-user@172.31.40.190 /opt/tomcat8/bin/startup.sh"
                }
            }
        }
    }
}