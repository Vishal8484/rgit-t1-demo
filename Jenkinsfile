pipeline{
    agent any
    tools{
        maven 'local_maven'
    }

    stages{
        stage('Build'){
            sh 'mvn clean package'
        }
        post{
            success{
                echo "Archiving the artifacts"
                archieArtifacts artifacts: '**target/*.war'
            }
        }
        stage('Deploy to Tomcat server'){
            steps{
                deploy adapters: [tomcat9(path: '', url: 'http://localhost:8081/')], contextPath: null, war: '**/*.war'
            }

        }
    }
}