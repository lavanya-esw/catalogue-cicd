@Library('jenkins-shared-library') _
def configMap= [
    project:"roboshop",cd 
    component:"catalogue"
]

if( ! env.BRANCH_NAME.equalsIgnore(main)){
    nodejsEKSpipeline(configMap)
}
else{
    echo "Please follow the CR process"
}