pipeline{
    agent{
        node{
            label 'AGENT-1'
        }
    }
    environment{
        appVersion = ""
    }
    stages{
        stage('Read Version'){
            steps{
                script{
                    def packageJSON = readJSON file : 'package.json'
                    appVersion = packageJSON.version
                    echo "app version:${appVersion}"
                }
            }
        }
        stage('Install Dependencies') {
            steps {
                script{
                    sh """
                        npm install
                    """
                }
            }
        }
        stage('build'){
            environment{
                ACC_ID = "500532068743"
                PROJECT = "roboshop"
                COMPONENT = "catalogue"
            }
            steps{
                script{
                    wwithAWS(region:'us-east-1',credentials:'aws-access'){
                        sh """
                            aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin ${ACC_ID}.dkr.ecr.us-east-1.amazonaws.com
                            docker build -t ${ACC_ID}.dkr.ecr.us-east-1.amazonaws.com/${PROJECT}/${COMPONENT}:${appVersion}
                            docker images
                            docker push ${ACC_ID}.dkr.ecr.us-east-1.amazonaws.com/${PROJECT}/${COMPONENT}:${appVersion}
                        """
                    }
                }
            }
        }
        stage('test'){
            steps{
                script{
                    sh """
                        echo "testing..."
                    """
                }
            }
        }
        stage('deploy'){
            steps{
                script{
                    sh """
                        echo "deploying"
                    """
                }
            }
        }
    }
    post{
        always{
            cleanWs()
        }
    }
}