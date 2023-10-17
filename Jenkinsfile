pipeline {
    agent any

    stages {
        stage('GIT') {
            steps {
                echo "Getting project from git"
                git 'https://github.com/ahmedbalti/5sae6_groupe5_kaddem/new/NihedAttia-5sae6-G5'
            }
        }

        stage('MVN CLEAN') {
            steps {
                sh 'mvn clean'
            }
        }

        stage('MVN Compile') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('MVN SonarQube') {
            steps {
                withSonarQubeEnv('sonarqube-10.2.1') { 
                sh "mvn sonar:sonar"
                }
            }
        }
    }

    post {
        success {
            echo 'Build and analysis successfully completed.'
        }
        failure {
            echo 'Build or analysis failed. Please check the logs for more details.'
        }
    }
}