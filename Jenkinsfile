pipeline {

    agent any
    stages {

        stage('Build'){
            steps{
                sh 'echo probando'
                sh 'mkdir lib'
                sh 'cd lib/ ; wget https://repo1.maven.org/maven2/org/junit/platform/junit-platform-console-standalone/1.9.3/junit-platform-console-standalone-1.9.3.jar'
                sh 'cd src ; javac -cp "../lib/junit-platform-console-standalone-1.9.3.jar" CarTest.java Car.java App.java'
            }
        }

        stage('Test'){
            steps{
                sh 'cd src/ ; java -jar ../lib/junit-platform-console-standalone-1.9.3.jar -cp "." --select-class CarTest --reports-dir="reports"'
                junit 'src/reports/*-jupiter.xml'
            }
        }

        stage('Deploy'){
            steps{
                sh 'cd src/ ; java App' 
            }
        }
    }

}
