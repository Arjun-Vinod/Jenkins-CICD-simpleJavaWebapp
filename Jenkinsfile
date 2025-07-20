pipeline{
    agent any
    stages{
        stage('Continuous Download'){
            steps{
                git branch: 'main', url: 'https://github.com/Arjun-Vinod/Jenkins-CICD-simpleJavaWebapp.git'
            }
        }
        stage('Continuous Build'){
           steps{
                sh 'mvn package'
           }
        }
        stage('Continuous Deployment'){
            steps{
                sh 'scp /var/lib/jenkins/workspace/Pipeline_Job/webapp/target/webapp.war ubuntu@172.31.27.125:/var/lib/tomcat10/webapps/Testapp.war'
            }
        }
        stage('Continuous Testing'){
            steps{
                git branch: 'main', url: 'https://github.com/Arjun-Vinod/WebAppTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/Pipeline_Job/testing.jar'
            }
        }
        stage('Continuous Delivery'){
            steps{
                sh 'scp /var/lib/jenkins/workspace/Pipeline_Job/webapp/target/webapp.war ubuntu@172.31.31.120:/var/lib/tomcat10/webapps/Productapp.war'
            }
        }
    }
}
