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
                     withSonarQubeEnv(credentialsId: 'geolocation-24-sonarID') {
                sh 'mvn sonar:sonar'
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

