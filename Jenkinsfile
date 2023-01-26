pipeline {

    agent any
     tools {
  maven 'M2_HOME'
     }

    stages{
        stage('Git Checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/henrykrop2022/helloworld_jan_23.git'
            }
        }
        stage('UNIT Testing'){
            steps{
               sh 'mvn clean'
               sh 'mvn install -DskipTests'
               sh 'mvn package -DskipTests'
            }
        }
    }
}