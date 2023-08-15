pipeline {
    agent any
    stages {
        stage('1-EXECUTION') {
            steps {
                sh 'apt install -y python3-pip'
                sh 'pip install -r requirements.txt'
                sh 'chmod u+x hello.py'
                sh 'touch result.txt'
                sh 'python3 hello.py -n Dmitry > result.txt'
            }
        }
        stage('2-ARCHIVEARTIFACT') {
            steps {
                archiveArtifacts artifacts: 'result.txt'
            }
        }
    }
}
