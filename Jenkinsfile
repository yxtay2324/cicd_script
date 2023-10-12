def userDefContents
def parserDefContents
def defContentsDiffer

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
                script {
                    try {
                        sh "diff -q file1.txt file2.txt"
                        defContentDiffer = false
                        echo "No differences picked up on definitions"
                    }
                    catch (err) {
                        defContentDiffer = true
                        echo "Files content are different. ${err}"
                    }
                }
            }
        }

        stage('succeed check') {
            when {
                expression {
                    !defContentDiffer
                }
            }
            steps {
                 echo "Pushing API to server."
            }
        }

        stage('failed check') {
            when {
                expression {
                    defContentDiffer
                }
            }
            steps {
                echo "Rejecting API"
            }
        }
    }
}
