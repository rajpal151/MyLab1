pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }

    environment{
       ArtifactId = readMavenPom().getArtifactId()
       Version = readMavenPom().getVersion()
       Name = readMavenPom().getName()
       GroupId = readMavenPom().getGroupId()
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

        //stage 4 publish the artifacts to nexus
        stage ('Publish to Nexus'){
            steps {
                nexusArtifactUploader artifacts: 
                [[artifactId: "${ArtifactId}", 
                classifier: '', 
                file: 'target/VinayDevOpsLab-0.0.5-SNAPSHOT.war',
                 type: 'war']], 
                 credentialsId: 'c48edd7c-df4b-44a5-8712-93842829d6a9', 
                 groupId: "${GroupId}", 
                 nexusUrl: '192.168.1.2:8081', 
                 nexusVersion: 'nexus3', 
                 protocol: 'http', 
                 repository: 'VinayDevOpsLab-SNAPSHOT',
                  version: "${Version}"
          }
        }

        //Stage4: Print some information
        stage ('Print Environment Variables')
        {
            steps{
                echo "Artifact ID is '${ArtifactId}'"
                echo "Version is  '${Version}'"
                echo "Name is '${Name}'"
                echo "Group Id is '${GroupId}'"
            }
        }

        // Stage5 : Deploy
        stage ('Deploy'){
            steps {
                echo 'Deployment doing'
                }

            }
        }

    }       