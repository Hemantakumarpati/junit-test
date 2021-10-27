pipeline {
    agent any

       stages {
        stage('Build') {
            steps {
                git 'https://github.com/Hemantakumarpati/junit-test.git'
                sh './mvnw clean compile'
                // bat '.\\mvnw clean compile'
            }
        }
        stage('Test') {
            steps {
                sh './mvnw test'
                // bat '.\\mvnw test'
            }

            post {
                always {
                    junit '**/target/surefire-reports/TEST-*.xml'
                }
            }
        }
        stage('Publish') {
            steps {
                sh './mvnw package'
                // bat '.\\mvnw package'
            }
            post {
                success {
                    archiveArtifacts 'target/*.jar'
                    
                }
            }
        }
    }
}
