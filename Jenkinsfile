@Library("Shared") _
pipeline {
    agent { label "vinod" }
    
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage ("Code"){
            steps{
                script{
                  clone("https://github.com/pratik-001/django-notes-app.git","main")  
                }
                
            }
        }
        stage ("Build"){
            steps{
                script{
                   docker_build("notes-app", "latest", "pratdock05")
                }
                
            }
        }
        stage ("Push to Docker Hub"){
            steps{
                script{
                    docker_push("notes-app","latest","pratdock05")
                }
                }
        }
        stage ("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker compose down" && "docker compose up -d"
            }
        }
    }
}
