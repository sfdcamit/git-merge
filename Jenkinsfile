pipeline {
    agent any 
    stages {
        stage('Build & Deploy & Merge') { 
            steps {
                withAnt(installation: 'ANT_HOME') {
                    //for windows 
                    //bat "ant retrieve"
                    //bat "ant deploy"
                    //bat "cd deployComponent"
                    bat "git init"
                    bat "git add ."
                    bat "git status"
                    bat "git pull origin master"
                    bat "git add ."
                    bat "git commit -m \"testmessage\""
                    bat "git status"
                    bat "git push origin master"
                    bat "ant deploy"
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
