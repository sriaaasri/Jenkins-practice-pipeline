pipeline {

    agent any

    options{
        disableConcurrentBuilds() 
        timeout(time: 5 , unit: 'MINUTES')
        timestamps()
        buildDiscarder(
            logRotator(
                numToKeepStr: '4',
                artifactNumToKeepStr: '2'
            )
        )
    }

    
    parameters {
        string (
            name: 'NAME',
            defaultValue: "default"
        )
        string(
            name: 'project',
            defaultValue: 'hello-world'
        )
        booleanParam(
            name: 'RUN_TESTS',
            defaultValue: true
        )

        choice(
            name: 'Environment',
            choices: [
                'dev',
                'prod'
            ],
            description: "select your environment"
        )
    }

    environment{
        Environment = "${params.Environment}"
    }


    stages{
        stage("hello"){
            steps{
                sh """
                    echo "Hi ${NAME} . Project: ${project}"
                    echo "Run tests - ${RUN_TESTS}"
                """
                echo "${params.Environment}"
            }
        }

        stage("testing"){
            when{
                expression { params.RUN_TESTS }
            }
            steps{
                echo "Running tests"
            }
        }
        stage("prod Env deploy"){
            when {
                // expression { params.Environment == "prod"}
                environment name: "Environment" ,value: "prod"
            }
            steps{
                echo "Deploying in ${params.Environment}"
            }
        }

        stage("dev Env deploy"){
            when {
                // expression { params.Environment == "dev"}
                environment name: "Environment" , value: "dev"
            }
            steps{
                echo "Deploying in ${params.Environment}"
            }
        }
    }
}