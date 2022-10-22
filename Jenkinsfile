pipeline {
    agent { label ('JDK-11') }
    stages {
        stage('vcs') {
            steps {
                git url: "https://github.com/satishnamgadda/python-webcount.git",
                    branch: "master"
            }
        }
        stage("build") {
            steps {
                sh 'pip3 install -r requirements.txt'
                sh 'tox'
            }
        }
        stage('artifacts') {
            steps {
                archiveArtifacts artifacts: '.tox/dist/webcount-0.1.zip', followSymlinks: false
            }
        }
        stage('juint results') {
            steps {
                junit '**/*.xml'
            }
        }

        }
    }
