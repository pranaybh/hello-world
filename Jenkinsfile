pipeline {
    agent none
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'maven:3.8.6-openjdk-8'
                }
            }
            steps {
                git 'https://github.com/pranaybh/hello-world.git'
                sh 'mvn --version'
                sh 'mvn clean package'
            }
        }
    }
}
