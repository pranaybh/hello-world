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
        stage('Bake') {
           agent { Dockerfile { additionalBuildArgs '-t newwebapp:$BUILD_NUMBER' } }
           steps {
               sh 'docker image ls'
		}
	  }
    }
}
