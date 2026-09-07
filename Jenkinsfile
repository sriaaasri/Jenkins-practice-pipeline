pipeline {

    agent any

    parameters {
        string (
            name: 'NAME',
            defaultValue: "default"

        )
    }

    stages{
        stage("hello"){
            steps{
                sh """
                    echo "Hi ${NAME}"
                """
            }
        }
    }
}