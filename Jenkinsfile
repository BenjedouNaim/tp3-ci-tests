pipeline {
    agent any

    environment {
        // Jenkins tourne en service (LocalSystem) : on ajoute Python et .NET au PATH
        PATH+PYTHON = "C:\\Users\\naimb\\AppData\\Local\\Programs\\Python\\Python314;C:\\Users\\naimb\\AppData\\Local\\Programs\\Python\\Python314\\Scripts;C:\\Program Files\\dotnet"
    }

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
