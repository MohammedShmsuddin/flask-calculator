pipeline {
    agent { docker { image 'python:3.7.2' } }
    stages {
        stage('build') {
            steps {
                // Run venv
                sh 'python3 -m venv env'
                sh 'source env/bin/activate'

                // Run pip install
                sh "pip3 install -r requirements.txt"

            }
        }
        stage('test') {
            steps {
                sh 'python3 -m unittest TestCalc.py'
            }
        }
    }
}