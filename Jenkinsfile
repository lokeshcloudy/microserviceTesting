def gv 
pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
        stage("init") {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }
        stage("test") {
            steps {
                script {
                    gv.buildApp()
                }
            }
        }
        stage("DockerLogin") {
            steps {
                script {
                    gv.dockerLogin()
                }
            }
        }
        stage("DockerBuild") {
            steps {
                script {
                    gv.dockerBuild()
                }
            }
        }
        stage("DockerPush") {
            steps {
                script {
                    gv.dockerPush()
                }
            }
        }
        stage("Deploy") {
            steps {
                script {
                    gv.deployApp()
                }
            }
        }
        
    }
}