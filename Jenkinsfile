pipeline {
    agent any

    stages {
        stage("Build Docker Images") {
            steps {
                sh "./gradlew buildDockerImage"
            }
        }

        stage("Publish Docker Image") {
            when {
                anyOf {
                    branch 'master'
                    branch 'release*'
                }
            }
            steps {
                sh "./gradlew pushDockerImage"
            }
        }
    }
}