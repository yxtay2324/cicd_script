def userDefContents
def parserDefContents

pipeline {
    agent any
    
    stages {
        stage("create text files") {
            steps {
                sh "printf 'texts1' > file1.txt"
                sh "printf 'texts2' > file2.txt"
            }            
        }

        stage("read files") {
            steps {
                script {
                    userDefContents = readFile 'texts1.txt'
                    parserDefContents = readFile 'texts2.txt'
                }
            }
        }

        stage("comparing defs") {
            steps {
                echo userDefContents
                echo parserDefContents
            }
        }
    }
}
