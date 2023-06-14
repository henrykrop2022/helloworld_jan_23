pipeline{
    agent any
    tools{
        maven 'M2_HOME'
    }
}
environment {
    registry= '880385147960.dkr.ecr.us-east-1.amazonaws.com/helloworld_jan_23'
    registryCredential = 'aws_jenkins'
    dockerimage = ''
}
stages{
    stage('check out'){
        steps{
            git branch: 'main', url: 'https://github.com/henrykrop2022/helloworld_jan_23.git'
        }
    }
    stages{
        stage('Code Build'){
            steps{
                sh 'mvn clean package'
            }
        }
        stage{
            steps('Test'){
                sh 'mvn test'
            }
        }
    }
    
}