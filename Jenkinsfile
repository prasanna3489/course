pipeline{
    agent any
    tools {
        maven "maven39"
    }
    stages{
        stage('scm checkout'){
            steps{
                git 'https://github.com/prasanna3489/course.git'
            }
        }
        stage('build'){
            steps{
                sh "mvn clean package"
            }
        }
        stage('test'){
            steps{
                sh "mvn test"
            }
        }
        stage('sonarqube analysis'){
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'sonar_token') {
                        sh "mvn sonar:sonar"
                    }
                }
            }
        }
    }
}
