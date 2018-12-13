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
    post {
        always {
            echo 'I will always say Hello again!'
            echo currentBuild.currentResult;
            emailext body: "${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}\n More info at: ${env.BUILD_URL}",
                recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']],
                subject: "Jenkins Build ${currentBuild.currentResult}: Job ${env.JOB_NAME}"
            
        }
        publishHTML(
            [
                allowMissing: true, 
                alwaysLinkToLastBuild: false, 
                keepAll: false, 
                reportDir: 'C:\\Users\\amitsingh4\\Documents\\Reports', 
                reportFiles: 'index.html, index1.html', 
                reportName: 'HTML Report', 
                reportTitles: '${currentBuild.currentResult}: Job ${env.JOB_NAME} build ${env.BUILD_NUMBER}'
            ]
        )
    }
}
