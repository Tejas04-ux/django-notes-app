@Library("shared") _
pipeline{
    
    agent { label "Tejas"}
    
    stages{
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        
        stage("Build"){
            steps{
                sh "sudo rm -rf data"
                script{
                docker_build("notes-app", "latest","tejasachari04")    
                }
            }   
        }
        stage("code"){
    steps{
        script{
            git url: "https://github.com/Tejas04-ux/django-notes-app.git", branch: "main"
        }
    }
}
        stage("Push to dockerhub"){
            steps{
                script{
                    docker_push("notes-app", "latest", "tejasachari04")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose up -d"
            }
        }
    } 
}
