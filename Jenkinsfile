pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                script {
                    withAWS(credentials: "aws-creds") {
                        def test_output = sh(script: "aws s3 ls", returnStdout: true)
                        println(test_output)
                    }
                }
            }
        }
    }
}