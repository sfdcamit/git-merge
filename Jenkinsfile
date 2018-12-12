pipeline {
    agent any 
    stages {
        stage(' Build Stage ') { 
            steps {
                echo "This is build Stage"
                withAnt(installation: 'ANT_HOME') {
                    // for windows batch command..
                    bat "ant retrieve"
                    bat "ant deploy"
                    //bat "cd deployComponent"
                    //bat "git init"
                    //bat "git add ."
                    //bat "git status"
                    //bat "git checkout Ananya"
                    //bat "git ls-tree --name-only Ananya"
                    //bat "git pull origin master"
                    //bat "git status"
                    //bat "git pull origin master"
                    //bat "git add ."
                    //bat "git commit -m \"testmessage\""
                    //bat "git checkout master"
                    //bat "git merge Ananya"
                    //bat "git status"
                    //bat "git checkout master"
                    //bat "ant deploy"
                }
                
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
