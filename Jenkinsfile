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
        stage('build'){
            steps{
                script{
                    sh """
                        echo "buiding..."
                    """
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
}