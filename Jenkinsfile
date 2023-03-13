pipeline{
    agent{ label 'SG_Jenkins_Docker' }
    triggers { pollSCM ('* * * * *') }
    stages{
        stage('Version Control System'){
            steps{
                git url: 'https://github.com/Sagautam/StudentCoursesRestAPI.git'
                branch: 'develop'
            }
        }
        stage('Build Docker Image'){
            steps{
                sh 'docker image build -t sagautam/spc:latest .'
            }
        }
        stage('Scan Docker Image using SNYK'){
            steps{
                sh 'docker scan sagautam/spc'
            }
        }
        stage('Push Docker Image'){
            steps{
                sh 'docker image push sagautam/spc:latest'
            }
        }
    }
}