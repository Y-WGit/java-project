
properties([pipelineTriggers([githubPush()])]) 

node('linux'){
    
    stage('Unit Tests'){
//The pipeline will initiate unit tests using ant and create a junit report. 
//The shell command to run ant tests is ant -f test.xml -v
//The junit report source data is located in reports/result.xml
        ant -f test.xml -v
        junit 'reports/result.xml'
    }
    
    stage('Build'){
        git 'https://github.com/Y-WGit/java-project.git'
        sh "ant"
    }
    
    stage('Test'){
        sh "ant -buildfile test.xml"
    }
    
    stage('Reports'){
        junit 'reports/*.xml'
    }
}
