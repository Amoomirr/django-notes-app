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
                build("notes-app","shared")
            }
        }
        }
         stage("Push To DockerHub") {
    steps {
        script{
            push("notes-app","shared","amoomirr")
        }
    }
}
        stage('Deploy') {
            steps {
                sh "docker compose down && docker compose up -d"
                echo "Deployment done"
            }
        }
    }
}

       
