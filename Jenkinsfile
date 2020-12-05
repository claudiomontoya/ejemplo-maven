pipeline {
    agent any

    stages {
        stage('compile') {
            steps {
                  sh './mvnw clean compile -e'    
            }
        }
        stage('test'){
            steps {
                    sh './mvnw clean test -e'
            }
        }
        stage('jar'){
            steps {
                    sh './mvnw clean package -e'
            }
        }
	stage('SonarQube analysis') {
           steps {
             withSonarQubeEnv(installationName: 'sonar') { 
             sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
             }
          }
        } 
        stage('run'){
            steps {
                   sh 'nohup bash ./mvnw spring-boot:run &'
            }
        }
        stage('Curl') {
	    steps {
		  sh 'sleep 20'
		  sh 'curl -X GET http://localhost:8081/rest/mscovid/test?msg=testing &'
		  }
	}
    }
}
