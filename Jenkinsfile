pipeline{
    agent any
    tools{
        maven 'M2_HOME'
    }
    environment {
        imagename = "henryrop/helloworld_jan_23"
         registryCredential = 'henryrop-dockerhub'
    }
    stages{
        stage('check out'){
            steps{
                git branch: 'main', url: 'https://github.com/henrykrop2022/helloworld_jan_23.git'
                }
            }   
        stage('Code Build'){
                steps{
                    sh 'mvn clean package'
            }
        }
        stage('Test'){
                steps{
                    sh 'mvn test'
            }
        } 
        stage('Sonar Analysis'){
            steps{
                script{
                     withSonarQubeEnv(credentialsId: 'hello-world-tokenID') {
                sh 'mvn sonar:sonar -Dsonar.token=myAuthenticationToken'
                     }
                 }
             }
         }     
        stage('Build Image'){
            steps{
                script{
                    dockerImage = docker.build imagename
                }
            }
        }     
    }  
} 

