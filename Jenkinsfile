pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                script {
                    withAWS(credentials: "aws-creds") {
                        // def test_output = sh(script: "aws s3 ls", returnStdout: true)
                        kms_output = cfnUpdate(stack:"test-kms-stack", file:"test-kms.template")
                        println(kms_output)
                        println(kms_output.getClass())
                        kms_output_id = kms_output["testKmsKeyOutput"]
                        println(kms_output_id)
                        println(kms_output_id.getClass())
                        withAWS(region: "ap-southeast-2") {
                            cfnUpdate(stack:"test-kms-stack-replica", paramsFile:"test-kms.json", file:"test-kms-replica.template")
                        }
                    }
                }
            }
        }
    }
}