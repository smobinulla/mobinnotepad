pipeline{
    agent any
    stages{
        stage("PullCode"){
            steps {
                echo "Cloning Source Code"
                git url: "https://github.com/smobinulla/mobinnotepad.git", branch: "main"
            }
        }
        stage("BuildCode"){
            steps {
                echo "Buildin Docker Image"
                sh "docker build -t mobinnotepad ."
            }
        }
        stage("Push Code to Docker Hub"){
            steps {
                echo "Pushing Image to DockerHub"
                withCredentials([usernamePassword(credentialsId:"DockerHub", passwordVariable:"dockerHubPass", usernameVariable:"dockerHubUser")]){
                sh "docker tag mobinnotepad ${env.dockerHubUser}/mobinnotepad:latest"
                sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                sh "docker push ${env.dockerHubUser}/mobinnotepad:latest"    
                }
                
            }
        }
        stage("DeployCode"){
            steps {
                echo "Deploying Notepad App"
                sh "docker-compose down && docker-compose up -d"
            }
            
        }
        
    }
    
} 
