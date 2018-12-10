pipeline {
    agent any 
    stages {
        stage('Build & Deploy') { 
            steps {
                withAnt(installation: 'ANT_HOME') {
                    //for windows 
                    //bat "ant retrieve"
                    //bat "ant deploy"
                    //bat "cd deployComponent"
                    bat "git init"
                    bat "git add ."
                    bat "git status"
                }
                echo "This is build Stage"
            }
        }
        stage('Compile') { 
            steps {
                input('do you want to proceed?')
            }
        }
        stage('Testing Stage'){
            parallel{
                stage('unit test'){
                    steps{
                        echo "unit tes is running"
                    }
                }
                stage('Integration Test'){
                    steps{
                        echo "Integration Test is running"
                    }
                }
            }
        }
        stage('Commit to Feature Branch') { 
            steps {
                echo "Commiting to Feature Branch...." 
            }
        }
    }
}
