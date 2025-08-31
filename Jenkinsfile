pipeline{
    agent {label 'Pradeep'}
    stages{
        stage("code clone"){
            steps{
                git url: "https://github.com/ChitrolyaPradeep/node-todo-cicd.git", branch: "master"
                echo "code clone ho gya"
            }
        }
        stage("code build"){
            steps{
                sh "docker build -t node-app:v3 ."
                echo "code build ho gya"
                
            }
        }
        stage("image push"){
            steps{
                withCredentials([usernamePassword(credentialsId:"Pradeep",usernameVariable:"yashwant",passwordVariable:"nandni")]){
                sh "docker login -u ${env.yashwant} -p ${env.nandni} "
                sh "docker tag node-app:v3 ${env.yashwant}/node-app:v4"
                sh "docker push ${env.yashwant}/node-app:v4"
                }
                echo "image push ho gya"
            }
        }
        stage("code deploy"){
            steps{
                sh "docker-compose down && docker-compose up -d"
                echo "code deploy ho gya"
                
            }
        }
    }
}      
