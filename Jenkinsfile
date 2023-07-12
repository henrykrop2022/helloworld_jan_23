pipeline{
    agent any
    tools{
        maven 'M2_HOME'
    }
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
        stage('Test'){
            steps{
                sh 'mvn test'
            }
        }
        stage('Build Image'){
            steps{
                script{
                    dockerImage = docker.build registry +":$BUILD_NUMBER"
                }
            }
        }
        // stage('Deploy Image'){
        //     steps{
        //         script{
        //             docker.withRegistry("https://"+registry,"ecr:us-east-1:"+registryCredential) {
        //                 dockerImage.push()
        //             }
        //         }
        //     }
        // }
    }
    
}
