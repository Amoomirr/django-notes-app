@Library('Shared')_
pipeline{
    agent { label 'amir'}
    stages{
         stage("Code") {
            steps {
                script {
                    clone("https://github.com/Amoomirr/django-notes-app.git","main")
            }
        }
        }
        stage('Build') {
            steps {
                script{
                build("notes-app","v3")
            }
        }
        }
         stage("Push To DockerHub") {
    steps {
        script{
            push("notes-app","v3","amoomirr")
        }
    }
}
        stage('Deploy') {
            steps {
                sh "docker compose down && docker compose up -d"
                echo "Deployment is done"
            }
        }
    }
}

       
