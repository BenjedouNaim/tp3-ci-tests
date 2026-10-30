pipeline {
    agent any


    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/BenjedouNaim/tp3-ci-tests.git'
            }
        }

        stage('Run .NET tests') {
            steps {
                dir('dotnet-app.Tests') {
                    bat 'dotnet test --logger "console;verbosity=detailed"'
                }
            }
        }

        stage('Run Python tests') {
            steps {
                dir('python-app') {
                    bat 'python -m pip install unittest-xml-reporting'
                    bat 'python -m unittest -v'
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished !!!'
        }
    }
}
