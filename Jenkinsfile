pipeline{
  //Directives
    agent any
    tools{

    }
    stages{
        //stage1: Build
        stage ('Build'){
            steps{
                sh 'mvn clean install package'
            }
        }

        //stage2: Testing
        stage ('Test'){
            steps
            {
                echo 'testing.......'
            }
        }

        //stage3: Deploying
        stage ('Deploy'){
            steps{
                echo 'deploying.......'
            }
        }

    }
}
