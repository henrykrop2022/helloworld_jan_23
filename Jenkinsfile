pipeline {

    agent any

    stages{
        stage('Git Checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/henrykrop2022/helloworld_jan_23.git'
            }
        }
        stage('UNIT Testing'){
            steps{
               sh 'mvn test'
            }
        }
    }
}