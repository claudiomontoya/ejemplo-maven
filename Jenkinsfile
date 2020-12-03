pipeline {
    agent any

    stages {
        stage('compile') {
            steps {
                dir("/Users/claudiomontoya/Documents/DiplomadoDevops/Maven/ejemplo-maven"){
                     sh './mvnw clean compile -e'
                }
               
            }
        }
        stage('test'){
            steps {
                 dir("/Users/claudiomontoya/Documents/DiplomadoDevops/Maven/ejemplo-maven"){
                    sh './mvnw clean test -e'
                 }
            }
        }
        stage('jar'){
            steps {
                 dir("/Users/claudiomontoya/Documents/DiplomadoDevops/Maven/ejemplo-maven"){
                    sh './mvnw clean package -e'
                 }
            }
        }
        stage('run'){
            steps {
                 dir("/Users/claudiomontoya/Documents/DiplomadoDevops/Maven/ejemplo-maven"){
                   sh 'nohup bash ./mvnw spring-boot:run &'
                 }
            }
        }
        stage('Curl') {
			steps {
				dir("/Users/claudiomontoya/Documents/DiplomadoDevops/Maven/ejemplo-maven"){
				    sh 'sleep 20'
					sh 'curl -X GET http://localhost:8081/rest/mscovid/test?msg=testing &'
				}
			}

		}
    }
}
