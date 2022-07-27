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
           agent { dockerfile { additionalBuildArgs '-t newwebapp:$BUILD_NUMBER' } }
           steps {
               sh 'ls -l'
		}
	  }
        stage('Deploy') {
          agent any
          steps {
              input(
                message: 'Deploy to production?',
                ok: 'Yes'
		 )
             sh 'docker container run -itd -p 8083:8080 newwebapp:$BUILD_NUMBER'
		}
	}
    }
}
