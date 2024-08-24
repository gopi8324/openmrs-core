pipeline {
    agent any
    options { 
        timeout(time: 30, unit: 'MINUTES') 
    }
    triggers {
        pollSCM('* * * * *')
    }
    stages {
        stage('git') {
            steps {
                git url: 'https://github.com/gopi8324/openmrs-core.git', 
                    branch: 'master'
            }
        }
        stage('build') {
            steps {
                sh 'mvn package'
                archiveArtifacts artifacts: '**/openmrs-*.jar'
                junit testResults: '**/TEST-*.xml'
            }
        } 
        
    }  
}
