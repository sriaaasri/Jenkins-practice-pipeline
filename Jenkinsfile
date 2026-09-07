pipeline {

    agent any

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
    }
}