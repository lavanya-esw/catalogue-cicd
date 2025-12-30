@Library('jenkins-shared-library@main') _
def configMap= [
    project:"roboshop",
    component:"catalogue"
]

if(!env.BRANCH_NAME.equalsIgnoreCase("main")){
    nodejsEKSpipeline(configMap)
}
else{
    echo "Please follow the CR process"
}
