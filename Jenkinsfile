pipeline {
    agent {
    label 'node1'
    }

    tools {
        maven 'maven' // This must match the name in Global Tool Configuration
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Add deployment steps here (e.g., copying JAR/WAR to a server)
                sh """
                   sudo docker run -d --name tomcat -p 8080:8080 tomcat
                   sudo docker cp target/*.war tomcat:/usr/local/tomcat/webapps
                """
            }
        }
    }
}
