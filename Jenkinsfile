pipeline {
    agent any

    parameters {
         string(name: 'tomcat_dev', defaultValue: '54.82.254.140', description: 'Staging Server')
         string(name: 'tomcat_prod', defaultValue: '54.86.220.201', description: 'Production Server')
    }

    triggers {
         pollSCM('* * * * *')
     }

stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage ('Deployments'){
            parallel{
                stage ('Deploy to Staging'){
                    steps {
                        bat "winscp -i /home/jenkins/tomcat-demo.pem **/target.
                    }
                }

                stage ("Deploy to Production"){
                    steps {
                        bat "winscp -i /home/jenkins/tomcat-demo.pem **/target.
                    }
                }
            }
        }
    }
}