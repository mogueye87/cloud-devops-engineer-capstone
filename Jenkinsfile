pipeline {
    agent any
    environment {
        DOCKER_IMAGE_NAME = "mogueye87/simple-webapp"
    }
    stages {
        stage('Build') {
            steps {
                echo 'Hello world'
                sh 'ls -lah'
            }
        }
        stage('Lint HTML') {
            steps {
                sh 'tidy -q -e *.html'
            }
        }

        stage('Build Docker Image') {
            when {
                branch 'master'
            }
            steps {
                script {
                    app = docker.build("mogueye87/simple-webapp")
                    app.inside {
                        sh 'echo $(curl localhost:8080)'
                    }
                }
            }
        }
        stage('Push Docker Image') {
            when {
                branch 'master'
            }
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker_hub_login') {
                        app.push("${env.BUILD_NUMBER}")
                        app.push("latest")
                    }
                }
            }
        }

        stage('Deploy to Kubernetes Cluster') {
            when {
                branch 'master'
            }
            steps {
                input 'Deploy to EKS Kubernetes Cluster?'
                milestone(1)
                kubernetesDeploy(
                kubeconfigId: 'kubeconfig',
                configs: 'nginx-webapp-kube.yml',
                enableConfigSubstitution: true  
                )
            }
        }
   }
}