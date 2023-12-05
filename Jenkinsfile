pipeline {
    agent any
    tools{
        nodejs "nodejs21"
    }

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    
        stage("connect git repository") {
            steps {
                script {
                    git branch: 'main', url: 'https://github.com/Laura-Eliise/KoodJohviCICD'
                }
            }
        }
    
        stage("npm install") {
            steps {
                script {
                    sh 'npm install'
                }
            }
        }
    
        stage("build application") {
            steps {
                script {
                    sh 'npm run build'
                }
            }
        }

        stage("deplay main application") {
            steps {
                script {
                    sh 'mkdir -p /kj_deployments/Laura-Eliise_main'
                }
            }
        }

        stage("deplay develop application") {
            steps {
                script {
                    sh 'mkdir -p /kj_deployments/Laura-Eliise_develop'
                }
            }
        }
        
        stage("copying build files to main") {
            steps {
                script {
                    sh 'cp -R dist/kood-johvi-cicd/browser/* /kj_deployments/Laura-Eliise_main'
                }
            }
        }

        stage("copying build files to develop") {
            steps {
                script {
                    sh 'cp -R dist/kood-johvi-cicd/browser/* /kj_deployments/Laura-Eliise_develop'
                }
            }
        }
    }
}
