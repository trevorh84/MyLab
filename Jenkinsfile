pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }

    environment {
        ArtifactId = readMavenPom().getArtifactId()
        Version = readMavenPom().getVersion()
        GroupId = readMavenPom().getGroupId()
        Name = readMavenPom().getName()
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
                nexusArtifactUploader artifacts: 
                [[artifactId: 'TrevorDevOpsLab', 
                classifier: '', 
                file: 'target/TrevorDevOpsLab-0.0.11-SNAPSHOT.war', 
                type: 'war']], 
                credentialsId: 'f4b71a2d-b33c-418e-82fd-cb0c8588a525', 
                groupId: 'com.trevordevopslab', 
                nexusUrl: '172.20.10.57:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'TrevorDevOpsSnapshot', 
                version: '0.0.11-SNAPSHOT'
            }

        }

        stage ('Printing environment variables') {
            steps {
                echo "Artifact id : '${ArtifactId}'" 
                echo "Version : '${Version}'" 
                echo "Group id : '${GroupId}'" 
                echo "Name is : '${Name}'" 
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