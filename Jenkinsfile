pipeline {
    agent any

    stages {
        stage('Check for changes') {
            steps {
                script {
                    def changes = sh(returnStdout: true, script: 'git diff --name-only HEAD^ HEAD')
                    if (changes.trim() != '') {
                        stage('Install dependencies') {
                            steps {
                                sh 'pip install -r requirements.txt'
                            }
                        }
                        
                        stage('Run hello.py') {
                            steps {
                                sh 'python hello.py --name=${params.STUDENT_NAME}'
                            }
                        }
                        
                        stage('Save output to result.txt') {
                            steps {
                                sh 'python hello.py --name=${params.STUDENT_NAME} > result.txt'
                            }
                        }
                        
                        stage('Archive result.txt') {
                            steps {
                                archiveArtifacts 'result.txt'
                            }
                        }
                    }
                }
            }
        }
    }
}
