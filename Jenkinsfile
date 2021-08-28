@Library('JenkinsSharedLibrary')_
pipeline {
    agent any
    tools {
        gradle 'Gradle'
    }
    stages {
        stage("test") {
            steps {
                script {
                    buildJar './gradlew -v'
                }
            }
        }
        stage("DockerLogin") {
            steps {
                script {
                    dockerLogin 'dockerhub'
                }
            }
        }
        stage("DockerBuild") {
            steps {
                script {
                    buildImage 'lokeshlish/app_test:1.0.0'
                }
            }
        }
        stage("DockerPush") {
            steps {
                script {
                    dockerPush 'lokeshlish/app_test:1.0.0'
                }
            }
        }
        stage("Deploy") {
            steps {
                script {
                    deployApp()
                }
            }
        }
        
    }
}
