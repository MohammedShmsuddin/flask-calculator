pipeline {
    agent { 
        node {
            label 'docker-agent-python'
            }
      }
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                pip install -r requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                python3 -m unittest TestCalc.py
                
                '''
            }
        }
        stage('Build Docker') {
            steps {
                echo 'Building docker image from Dockerfile....'
                sh '''
                
                sudo docker build -t flask-app .
                '''

            }
        }
        stage('Run Docker Container') {
            steps {
                echo 'Running Docker container......'
                sh '''
                
                sudo docker run -p 3000:3000 --name flask-app -d flask-app
                '''

            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                // sudo nohup python3 app.py > log.txt 2>&1 &
                '''
            }
        }
    }
}