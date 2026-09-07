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
    }

    stages{
        stage("hello"){
            steps{
                sh """
                    echo "Hi ${NAME} . Project: ${project}"
                """
            }
        }
    }
}