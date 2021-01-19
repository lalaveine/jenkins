pipeline {
    agent {
        docker {
            image 'python:3.8.0'
            args '-u root:root -p 8000:8000'
        }
    }

    stages {
        stage('Git') {
            steps {
                // checkout([$class: 'GitSCM', branches: [[name: '*/main']],
                // doGenerateSubmoduleConfigurations: false, extensions: [],
                // submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/vaytlou/PIS-LABS.git']]
                // ])
                git branch: 'master', url: 'https://github.com/vaytlou/PIS-LABS.git'
            }
        }
        stage('Test') {
            steps {
                sh 'python --version'
                sh 'python -m venv env'
                sh 'python -c "import this"'
                sh '. env/bin/activate'
                sh 'pip install --upgrade pip'
                sh 'pip install pytest'
                sh 'pip install -r Lab6/identidock/requirements.txt'
                sh 'cd Lab6/identidock/app'
                sh 'pytest'
            }
        }
    }
}
