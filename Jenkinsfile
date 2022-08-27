pipeline {
    agent any
    tools {nodejs "node16"}
    environment {
        NODE_ENV='production'
    }

    stages {
        stage('source') {
            steps {
                git ' https://github.com/lolucodes/aws_codebuild_codedeploy_nodeJs_demo.git'
                sh 'cat index.js'
            }
        }
        stage('build') {
            environment {
                NODE_ENV='staging'
            }
            steps {
                echo NODE_ENV
                withCredentials([string(credentialsId: 'f7e1b09d-58a7-4a4c-9533-cd579ee255d8', variable: 'secver')]) {
            // some block
            echo secver
            }
                sh 'npm install'
            }
        }
        stage('saveArtifact') {
            steps {
                archiveArtifacts artifacts: '**', followSymlinks: false
            }
        }
    }
}
