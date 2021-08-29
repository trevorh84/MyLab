pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }

    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'

            }
        }

        stage ('Publish to nexus') {
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'TrevorDevOpsLab', classifier: '', file: 'target/TrevorDevOpsLab-0.0.10-SNAPSHOT.war', type: 'war']], credentialsId: '', groupId: 'com.trevordevopslab', nexusUrl: '172.20.10.57:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'TrevorDevOpsSnapshot', version: '0.0.11-SNAPSHOT'
            }

        }


        // Stage3 : Publish the source code to Sonarqube
        stage ('Sonarqube Analysis'){
            steps {
              echo ' sonar qube......'
            }
        }

        
        
    }

}