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

        //stage 4 publish the artifacts to nexus
        stage ('Publish to Nexus'){
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/', type: 'war'], [artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/VinayDevOpsLab-0.0.4-SNAPHSHOT.war', type: 'war']], credentialsId: 'c48edd7c-df4b-44a5-8712-93842829d6a9', groupId: 'com.vinaysdevopslab', nexusUrl: '192.168.1.2:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'http://192.168.1.2:8081/repository/VinayDevOpsLab-SNAPSHOT/', version: '0.0.4'
          }
        }

        // Stage4 : Deploy
        stage ('Deploy'){
            steps {
                echo 'Deployment doing'
                }

            }
        }

    }       