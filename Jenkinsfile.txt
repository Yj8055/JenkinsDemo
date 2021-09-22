pipeline 
{
    agent any
    stages
    {
        stage('Hello')
        {
            steps{
                echo 'this is my first java pipeline job'
                 }
        }
        stage('java'){
            steps{
                sh "java -version"
            }
        }
        stage('Build') 
        {
            steps 
            {
                // Get some code from a GitHub repository
                git 'https://github.com/Yj8055/JenkinsDemo.git'
            }
        }
        stage('compile')
        {
            steps
            {
                sh"javac Hello.java"
            }
        }
        stage('run')
        {
            steps
            {
                sh"java Hello"
            }
        }
        stage('success')
        {
            steps
            {
                echo 'Job succeeded'
            }
        }
    }
}
