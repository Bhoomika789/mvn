pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
               git branch: 'main', url: 'https://github.com/Bhoomika789/mvn.git'
            }
        }
       stage('BUILD'){
    steps{
        bat """
        cd "E:\\aws & devops\\apache-maven-3.9.9\\bin"
        mvn clean install
        """
    }
}

    }
}
