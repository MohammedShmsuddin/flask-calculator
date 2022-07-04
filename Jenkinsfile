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
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                sudo nohup python3 app.py > log.txt 2>&1 &
                '''
            }
        }
    }
}