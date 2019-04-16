
properties([pipelineTriggers([githubPush()])]) 

node('linux'){
    
    stage('Unit Tests'){
//The pipeline will initiate unit tests using ant and create a junit report. 
//The shell command to run ant tests is ant -f test.xml -v
//The junit report source data is located in reports/result.xml
        sh "ant -f test.xml -v"
        junit 'reports/result.xml'
    }
    
    stage('Build'){
 //The pipeline will compile the Java application using ant.
 //The shell command to compile the application is ant -f build.xml -v    
        sh "ant -f build.xml -v"
    }
    
    stage('Test'){
        sh "ant -buildfile test.xml"
    }
    
    stage('Reports'){
        junit 'reports/*.xml'
    }
}
