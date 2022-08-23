def ENV
ENV = "dev"
pipeline {
    // default agent for all pipeline
    agent { label "JenkinsHosted" }

    options {
        skipStagesAfterUnstable()
    }
    environment {
        GIT_COMMIT_SHORT = sh(
                script: "printf \$(git rev-parse --short ${GIT_COMMIT})",
                returnStdout: true
        )
        ENV = "${ENV}"
    }
    stages {
        stage('Git info'){

            steps {
                 echo "--------------------GIT INFO-------------------------------"
                 echo "This is BRANCH: ${env.GIT_BRANCH}"
                 echo "This is PREVIOUS COMMIT: ${env.GIT_PREVIOUS_COMMIT }"
                 echo "This is CURRENT COMMIT: ${env.GIT_COMMIT }"
            }
        }

        stage('Build'){

            steps {
                 echo "--------------------Build-------------------------------"
                 sh 'pwd && cd examples/get-started/hello_world && cp -r /home/ubuntu/esp/hello_world/sdkconfig . && make'
            }
        }

    }
}
