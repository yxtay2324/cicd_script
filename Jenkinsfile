def userDefContents
def parserDefContents

pipeline {
    agent any

    stages {
        stage('create text files') {
            steps {
                sh 'touch file1.txt'
                sh 'touch file2.txt'
            }            
        }
    
        stage('input text files') {
            steps {
                sh "printf 'texts1' > file1.txt"
                sh "printf 'texts2' > file2.txt"
            }
        }
    
        stage('read files') {
            steps {
                script {
                    userDefContents = readFile 'file1.txt'
                    parserDefContents = readFile 'file2.txt'
                }
            }
        }
    
        stage('comparing defs') {
            steps {
                echo userDefContents
                echo parserDefContents
            }
        }
    }
}
