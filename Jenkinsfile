pipeline{
    agent any
    environment{
	  PATH = "${PATH}:${tool name: 'maven3', type: 'maven'}/bin"
	}
    stages{
        stage('SCM Checkout'){
<<<<<<< HEAD
            steps{
                git url: 'https://github.com/javahometech/6pmwebapp',
                branch: 'master',
                credentialsId: 'github'
            }
=======
            steps {
                git credentialsId: 'git-1', 
                url: 'https://github.com/git212/jenkins',
                branch: 'master'
                
                }
>>>>>>> a0ec284af2c4f88fa68cdcd48271cdf71289edda
        }

        stage('Maven Build'){
            steps{
                sh 'mvn clean package'
            }
        }

        stage('Deploy Dev'){
<<<<<<< HEAD
            steps{
                sshagent(['tomcat-dev']) {
                    // stop tomcat
                    sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.4.187 /opt/tomcat8/bin/shutdown.sh"
                    // copy war file to remote tomcat
                    sh "scp target/6pmwebapp.war  ec2-user@172.31.4.187:/opt/tomcat8/webapps/"
                    // start tomcat
                    sh "ssh ec2-user@172.31.4.187 /opt/tomcat8/bin/startup.sh"
                } 
=======
             steps{
                 sshagent(['tomcat-dev']) {
                    // stop tomcat
                    sh "ssh -o StrictHostKeyChecking=no ec2-user@13.232.74.26 /tomcat8/bin/shutdown.sh"
                    // copy war file to remote tomcat
                    sh "scp target/6pmwebapp.war  ec2-user@13.232.74.26:/tomcat8/webapps/"
                    // start tomcat
                    sh "ssh ec2-user@13.232.74.26 /tomcat8/bin/startup.sh"
                }
>>>>>>> a0ec284af2c4f88fa68cdcd48271cdf71289edda
            }
        }
    }
    post{
        success{
<<<<<<< HEAD
            mail body: """Hi Team, The app is successfully deployed
            ${BUILD_URL}

Thanks,
DevOps Team.
Java Home""", subject: "${JOB_NAME} - Successfully Deployed", to: 'kammana.hari@gmail.com'
        }

        failure{
            mail body: """Hi Team, The app deployment failed
            ${BUILD_URL}

Thanks,
DevOps Team.
Java Home""", subject: "${JOB_NAME} - Deployment failed", to: 'kammana.hari@gmail.com'
        }
    }
        
}
=======
           mail bcc: '', body: 'Successfully deployed jenkins', cc: '', from: '', replyTo: '', subject: 'sussfully deployed', to: 'mahantabharat312@gmail.com'
        }

    }        
}
>>>>>>> a0ec284af2c4f88fa68cdcd48271cdf71289edda
