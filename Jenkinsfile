pipeline {
    agent any
    tools { 
        maven 'maven' jdk 'java'
    }
    stages {
        stage("Clone project") {
            steps {
                script {
                    git credentialsId: "tghub_token1", url: "https://github.com/nnagibator228/mshp_devops_trigger"
                    sh 'ls -la'
                }
            }
        }
        stage("Scan project") {
            steps { 
                script {
                    withSonarQubeEnv(installationName: 'Mshp_Test', credentialsId: 'sonar1') {
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
    }
}
