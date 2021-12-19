pipeline {
    agent any
    // Mention tools that you are using in this declarative pipeline.
    tools {
        maven 'maven' // Tool name should be same as you mentioned in Jenkins maven installation under global tool configurations.
    }
    stages {
        stage('Clean & Compile') {
            steps {
                sh 'mvn clean compile' // This command cleans previous builds and compiles the code.
            }
        }
        stage('Build & Install') {
            steps {
                sh 'mvn install' // This command builds and installs packages/artifacts(.war) to maven local repository (~/.m2/repository).
            }
        }
        stage('Deploy') {
            steps {
                // In the below line replace the url to your tomcat webserver url to deploy artifact(.war) from maven local repository (~/.m2/repository) to tomcat server.
                deploy adapters: [tomcat9(credentialsId: 'Tomcat', path: '', url: 'http://13.233.195.96:8080/')], contextPath: null, onFailure: false, war: 'target/*.war'
            }
        }
    }
}
