pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
        stage ("Clean up") {
            steps {
                deleteDir()
            }
        }
        stage ("Clone repo") {
            steps {
                sh "git clone https://github.com/NefaZz/exp1.git"
            }
        }
        stage ("Generate backend image") {
            steps {
                dir("exp1") {
                    sh "mvn clean install"
                    sh "docker build -t docexp1-spring ."
                }
            }
        }
        stage ("Run docker compose") {
            steps {
                dir("exp1") {
                    sh "docker compose up -d"
                }
            }
        }
    }
}
